# 🔧 Most Common Prisma Issues & Solutions

_Based on 2,300+ GitHub issues and 3,776+ Stack Overflow questions_

### **🚨 Critical Issues (Production Breaking)**

#### **1. Migration & Schema Issues**
- **P3006**: Shadow database error (covered in our case study)
- **P3009**: Migration files missing or corrupted
- **P3014**: Schema drift detection
- **Database name with uppercase letters**: Migration failures
- **Data transformation during migrations**: Password encryption scenarios

**Solutions Pattern:**
```bash
# Check migration status
npx prisma migrate status

# Generate baseline migration for corrupted history
npx prisma migrate diff --from-empty --to-schema-datamodel prisma/schema.prisma --script

# Resolve migration conflicts
npx prisma migrate resolve --applied [migration_name]
```

#### **2. Engine & Runtime Issues**
- **Query Engine not found**: Platform-specific runtime issues
- **"Cannot find module @prisma/client/runtime"**: Bundle/deployment errors
- **RHEL/Alpine Linux**: Platform detection issues
- **Serverless deployment**: Engine bundling problems

**Solutions Pattern:**
```bash
# Force engine download for specific platform
npx prisma generate --generator client

# Set explicit platform in schema.prisma
generator client {
  provider = "prisma-client-js"
  binaryTargets = ["native", "rhel-openssl-1.0.x"]
}
```

#### **3. Connection & Environment Issues**
- **P1001**: Can't reach database server
- **Docker connection string**: Different URLs for inside/outside containers
- **SSL/TLS configuration**: Certificate issues
- **Connection pooling**: Too many connections

**Solutions Pattern:**
```env
# Environment-aware connection strings
DATABASE_URL_DEVELOPMENT="postgresql://user:pass@localhost:5432/db"
DATABASE_URL_DOCKER="postgresql://user:pass@postgres:5432/db"
DATABASE_URL_PRODUCTION="postgresql://user:pass@prod-host:5432/db?sslmode=require"
```

### **⚠️ Development Issues (Workflow Disrupting)**

#### **4. TypeScript Integration Problems**
- **req.user type issues**: Express middleware integration
- **Type safety with raw queries**: $queryRaw typing
- **Generated types**: Client regeneration problems
- **Next.js integration**: Multiple client instances

**Solutions Pattern:**
```typescript
// Express type augmentation
declare global {
  namespace Express {
    interface Request {
      user?: User; // Use Prisma-generated User type
    }
  }
}

// Proper client instantiation in Next.js
const globalForPrisma = globalThis as unknown as { prisma: PrismaClient };
export const prisma = globalForPrisma.prisma || new PrismaClient();
if (process.env.NODE_ENV !== 'production') globalForPrisma.prisma = prisma;
```

#### **5. Relationship & Query Issues**
- **Many-to-many querying**: Complex relationship filtering
- **N+1 query problems**: Performance degradation
- **JSON field querying**: String vs JSON type confusion
- **Nested create/update**: Transaction handling

**Solutions Pattern:**
```typescript
// Avoid N+1 with proper includes
const users = await prisma.user.findMany({
  include: {
    posts: {
      include: {
        comments: true,
      },
    },
  },
});

// Use relationJoins preview feature for better performance
// Enable in schema.prisma generator block
```

### **📊 Performance & Optimization Issues**

#### **6. Query Performance Problems**
- **Slow aggregations**: Large dataset handling
- **Missing indexes**: Composite index requirements
- **Connection pool exhaustion**: Too many concurrent connections
- **Large result sets**: Memory usage issues

**Solutions Pattern:**
```prisma
// Add composite indexes for common queries
model User {
  id       Int    @id @default(autoincrement())
  email    String
  status   String

  @@index([status, email]) // Composite index for filtering
  @@index([email]) // Single field index
}
```

#### **7. Development Workflow Issues**
- **prisma init stuck**: Network/proxy issues
- **Seed script not running**: Configuration problems
- **Studio connection**: VS Code vs browser access
- **Hot reload**: Client regeneration in development

**Solutions Pattern:**
```json
// package.json scripts
{
  "scripts": {
    "db:generate": "prisma generate",
    "db:migrate": "prisma migrate dev",
    "db:studio": "prisma studio",
    "db:seed": "tsx prisma/seed.ts"
  }
}
```

---

**Previous:** [C - Patterns and Anti-Patterns](./C-patterns-and-antipatterns.md)
**Next:** [E - Assessment and Certification](./E-assessment-and-certification.md)