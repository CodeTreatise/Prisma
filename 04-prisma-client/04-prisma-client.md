# 4. PRISMA CLIENT (Data Access Layer)

### 4.1 Setup & Configuration

- **4.1.1** Client Generation Process & Options
- **4.1.2** Type Safety Benefits & Generated Types
- **4.1.3** Custom Output Paths & Multi-client Setup
- **4.1.4** Client Instantiation & Singleton Patterns
- **4.1.5** Connection Management & Lifecycle

### 4.2 Basic CRUD Operations

- **4.2.1** Create Operations (`create`, `createMany`)
- **4.2.2** Read Operations (`findUnique`, `findFirst`, `findMany`)
- **4.2.3** Update Operations (`update`, `updateMany`, `upsert`)
- **4.2.4** Delete Operations (`delete`, `deleteMany`)
- **4.2.5** Count Operations & Aggregations

### 4.3 Advanced Queries & Filtering

- **4.3.1** Where Conditions & Operators
- **4.3.2** Logical Operators (AND, OR, NOT)
- **4.3.3** String & Text Filtering (contains, startsWith, endsWith)
- **4.3.4** Numeric & Date Filtering (gt, lt, gte, lte)
- **4.3.5** Array & List Filtering (in, notIn, has)
- **4.3.6** Null & Undefined Handling

### 4.4 Relations & Nested Operations

- **4.4.1** Including Related Data (`include`)
- **4.4.2** Selecting Specific Fields (`select`)
- **4.4.3** Nested Selections & Deep Includes
- **4.4.4** Filtering Relations & Nested Where
- **4.4.5** Nested Creates & Updates
- **4.4.6** Connect & Disconnect Operations

### 4.5 Raw SQL & Custom Queries

- **4.5.1** When to Use Raw SQL vs Generated Queries
- **4.5.2** `$queryRaw` for SELECT Operations
- **4.5.3** `$executeRaw` for INSERT/UPDATE/DELETE
- **4.5.4** `$queryRawUnsafe` for Dynamic Queries
- **4.5.5** Type Safety with Raw Queries
- **4.5.6** SQL Injection Prevention

### 4.6 Type Safety & Field Selection

- **4.6.1** Generated Types & Interfaces
- **4.6.2** Field Selection with Select
- **4.6.3** Partial Types & Optional Fields
- **4.6.4** Type Narrowing & Conditional Types
- **4.6.5** Custom Type Definitions
- **4.6.6** Runtime Type Validation

---

**Previous:** [03 - Prisma Schema](./03-prisma-schema.md)
**Next:** [05 - Prisma Migrate](./05-prisma-migrate.md)