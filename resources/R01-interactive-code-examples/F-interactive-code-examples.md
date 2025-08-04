# 💻 Interactive Code Examples

_Complete, executable examples for hands-on learning_

### **📚 Module 1: Foundations - Code Examples**

#### **1.1 First Prisma Setup**
```bash
# Initialize new project
mkdir my-prisma-app && cd my-prisma-app
npm init -y
npm install prisma @prisma/client
npm install -D typescript ts-node @types/node

# Initialize Prisma
npx prisma init
```

```typescript
// prisma/schema.prisma - Your first schema
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id    Int     @id @default(autoincrement())
  email String  @unique
  name  String?
  posts Post[]
}

model Post {
  id        Int     @id @default(autoincrement())
  title     String
  content   String?
  published Boolean @default(false)
  author    User    @relation(fields: [authorId], references: [id])
  authorId  Int
}
```

```typescript
// src/index.ts - Your first queries
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

async function main() {
  // Create user with posts
  const user = await prisma.user.create({
    data: {
      email: 'alice@example.com',
      name: 'Alice',
      posts: {
        create: [
          { title: 'Hello World', content: 'My first post' },
          { title: 'Learning Prisma', content: 'Prisma is awesome!' }
        ]
      }
    },
    include: { posts: true }
  })
  
  console.log('Created user:', user)
  
  // Find all users with their posts
  const users = await prisma.user.findMany({
    include: { posts: true }
  })
  
  console.log('All users:', JSON.stringify(users, null, 2))
}

main()
  .catch(console.error)
  .finally(() => prisma.$disconnect())
```

### **📚 Module 4: Prisma Client - Advanced Examples**

#### **4.1 Complex Filtering & Relations**
```typescript
// Complex queries with multiple filters and relations
async function complexQueries() {
  // Advanced filtering with AND/OR logic
  const posts = await prisma.post.findMany({
    where: {
      OR: [
        { title: { contains: 'prisma' } },
        { content: { contains: 'database' } }
      ],
      AND: [
        { published: true },
        { author: { email: { endsWith: '@company.com' } } }
      ]
    },
    include: {
      author: {
        select: { name: true, email: true }
      }
    },
    orderBy: [
      { createdAt: 'desc' },
      { title: 'asc' }
    ]
  })
  
  return posts
}
```

### **🚀 Quick Start Templates**

#### **Basic Express + Prisma API**
```bash
# Clone starter template
git clone https://github.com/prisma/express-prisma-starter.git
cd express-prisma-starter
npm install
cp .env.example .env
# Edit .env with your database URL
npx prisma migrate dev
npm run dev
```

---

**Previous:** [E - Assessment and Certification](./E-assessment-and-certification.md)
**Next:** [G - Real-World Case Studies](./G-real-world-case-studies.md)