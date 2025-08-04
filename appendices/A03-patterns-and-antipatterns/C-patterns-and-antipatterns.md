# 🎯 Prisma Patterns & Anti-Patterns

_Best practices vs common mistakes - based on real-world experience_

### **✅ RECOMMENDED PATTERNS**

#### **🏗️ Architecture Patterns**

##### **1. Repository Pattern with Dependency Injection**
```typescript
// ✅ Good: Clean separation with dependency injection
interface UserRepository {
  create(data: CreateUserData): Promise<User>;
  findById(id: string): Promise<User | null>;
  findByEmail(email: string): Promise<User | null>;
}

class PrismaUserRepository implements UserRepository {
  constructor(private prisma: PrismaClient) {}
  
  async create(data: CreateUserData): Promise<User> {
    return this.prisma.user.create({ data });
  }
  
  async findById(id: string): Promise<User | null> {
    return this.prisma.user.findUnique({ where: { id } });
  }
}

// Usage with dependency injection
class UserService {
  constructor(private userRepo: UserRepository) {}
  
  async registerUser(userData: RegisterData) {
    // Business logic here
    return this.userRepo.create(userData);
  }
}
```

##### **2. Transaction Management Pattern**
```typescript
// ✅ Good: Proper transaction handling
async function transferFunds(fromId: string, toId: string, amount: number) {
  return await prisma.$transaction(async (tx) => {
    // All operations in same transaction
    const fromAccount = await tx.account.update({
      where: { id: fromId },
      data: { balance: { decrement: amount } }
    });
    
    const toAccount = await tx.account.update({
      where: { id: toId },
      data: { balance: { increment: amount } }
    });
    
    // Automatic rollback if any operation fails
    return { fromAccount, toAccount };
  });
}
```

##### **3. Error Handling Pattern**
```typescript
// ✅ Good: Comprehensive error handling
import { Prisma } from '@prisma/client';

function handlePrismaError(error: unknown) {
  if (error instanceof Prisma.PrismaClientKnownRequestError) {
    switch (error.code) {
      case 'P2002':
        throw new ConflictError('Unique constraint violation');
      case 'P2025':
        throw new NotFoundError('Record not found');
      case 'P2003':
        throw new ValidationError('Foreign key constraint failed');
      default:
        throw new DatabaseError(`Database error: ${error.message}`);
    }
  }
  throw new UnknownError('An unexpected error occurred');
}
```

### **❌ ANTI-PATTERNS (What NOT to Do)**

#### **🚫 Query Anti-Patterns**

##### **1. N+1 Query Problem**
```typescript
// ❌ Bad: N+1 query problem
async function getBadUserPosts() {
  const users = await prisma.user.findMany();
  const usersWithPosts = [];
  
  for (const user of users) {
    const posts = await prisma.post.findMany({
      where: { authorId: user.id }
    });
    usersWithPosts.push({ ...user, posts });
  }
  
  return usersWithPosts; // Creates N+1 queries!
}

// ✅ Good: Single query with include
async function getGoodUserPosts() {
  return await prisma.user.findMany({
    include: {
      posts: true
    }
  });
}
```

##### **2. Missing Transaction for Related Operations**
```typescript
// ❌ Bad: Race conditions possible
async function badCreateUserAndProfile(userData: UserData) {
  const user = await prisma.user.create({ data: userData });
  
  // If this fails, user is already created!
  const profile = await prisma.profile.create({
    data: { userId: user.id, ...profileData }
  });
  
  return { user, profile };
}

// ✅ Good: Atomic transaction
async function goodCreateUserAndProfile(userData: UserData) {
  return await prisma.$transaction(async (tx) => {
    const user = await tx.user.create({ data: userData });
    const profile = await tx.profile.create({
      data: { userId: user.id, ...profileData }
    });
    return { user, profile };
  });
}
```

---

**Previous:** [B - Internal Architecture](./B-internal-architecture.md)
**Next:** [D - Common Issues and Solutions](./D-common-issues-and-solutions.md)