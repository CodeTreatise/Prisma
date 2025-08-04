# 🔧 Prisma Internal Architecture Deep Dive

_Understanding how Prisma works under the hood_

### **🏗️ Engine Architecture Overview**

#### **Core Components:**

```
Prisma Architecture
├── Prisma CLI (Node.js)
│   ├── Schema Parser
│   ├── Migration Engine Interface
│   └── Generator Orchestrator
├── Query Engine (Rust Binary)
│   ├── SQL Query Builder
│   ├── Connection Pool Manager
│   └── Type Validator
├── Migration Engine (Rust Binary)
│   ├── Schema Differ
│   ├── DDL Generator
│   └── Migration Executor
└── Prisma Client (Generated TypeScript)
    ├── Type-safe API
    ├── Runtime Query Builder
    └── Engine Communication Layer
```

#### **Communication Flow:**
1. **Schema.prisma** → Parser → **AST (Abstract Syntax Tree)**
2. **AST** → Code Generator → **Prisma Client**
3. **Client Calls** → Query Engine → **SQL Generation**
4. **SQL** → Database → **Results** → Type-safe Response

### **🔄 Migration Engine Deep Dive**

#### **Schema Diffing Algorithm:**

```
Current Schema → Parser → Schema AST
Target Schema → Parser → Target AST
                ↓
        Difference Calculator
                ↓
    ┌─────────────────────────┐
    │  Schema Differences     │
    │ ├── Added Models        │
    │ ├── Removed Models      │
    │ ├── Modified Fields     │
    │ └── Index Changes       │
    └─────────────────────────┘
                ↓
        DDL Generator
                ↓
        SQL Migration File
```

#### **Shadow Database Process:**

```
1. Create temporary database (shadow)
2. Apply current migrations to shadow
3. Apply new schema to shadow
4. Compare shadow vs target
5. Generate migration SQL
6. Cleanup shadow database
```

---

**Previous:** [A - Introduction and Setup](./A-introduction-and-setup.md)
**Next:** [C - Patterns and Anti-Patterns](./C-patterns-and-antipatterns.md)