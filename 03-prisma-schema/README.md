# Module 3: Prisma Schema (Data Modeling)

## 📋 Module Overview
- **Duration**: 3-4 hours
- **Prerequisites**: 
  - Completed Module 2: Getting Started
  - Understanding of database fundamentals
  - Basic knowledge of data modeling concepts
  - Familiarity with TypeScript syntax
- **Learning Objectives**: 
  - Master Prisma schema syntax and structure
  - Design efficient data models and relationships
  - Implement advanced data types and attributes
  - Create complex relationship patterns
  - Apply schema design best practices and performance optimization
- **Assessment Type**: Schema Design Project + Relationship Modeling Quiz
- **Difficulty Level**: Intermediate to Advanced
- **Next Module**: [04-prisma-client.md](../04-prisma-client/04-prisma-client.md)

---

## 🎯 What You'll Learn

By the end of this module, you will:
- ✅ Master Prisma schema file organization and syntax
- ✅ Configure generators and datasources effectively
- ✅ Design efficient data models with proper field types
- ✅ Implement all relationship patterns (1:1, 1:M, M:M, self-relations)
- ✅ Use advanced data types and custom attributes
- ✅ Apply schema introspection and validation techniques
- ✅ Follow data modeling best practices for performance
- ✅ Plan migration strategies for schema evolution

---

## 📚 Table of Contents

### [3.1 Schema Overview & Structure](./3.1-schema-overview-structure/README.md)
- ⏳ 3.1.1: Schema File Organization & Syntax
- ⏳ 3.1.2: Generator & Datasource Blocks Configuration
- ⏳ 3.1.3: Comments & Documentation Best Practices
- ⏳ 3.1.4: Schema Formatting & Validation
- ⏳ 3.1.5: Multi-file Schema Organization (Preview)

### [3.2 Data Model & Models](./3.2-data-model-models/README.md)
- ⏳ 3.2.1: Model Declaration & Naming Conventions
- ⏳ 3.2.2: Field Types & Modifiers
- ⏳ 3.2.3: Optional vs Required Fields
- ⏳ 3.2.4: Default Values & Auto-generation
- ⏳ 3.2.5: Model Attributes (@@map, @@index, @@unique)

### [3.3 Data Types & Attributes](./3.3-data-types-attributes/README.md)
- ⏳ 3.3.1: Scalar Types (String, Int, Boolean, DateTime, etc.)
- ⏳ 3.3.2: Special Types (Json, Bytes, Decimal)
- ⏳ 3.3.3: Field Attributes (@id, @unique, @default, @map)
- ⏳ 3.3.4: PostgreSQL-Specific Types (Json vs Jsonb)
- ⏳ 3.3.5: Enums & Custom Types

### [3.4 Relationships & Relations](./3.4-relationships-relations/README.md)
- ✅ 3.4.1: One-to-One Relationships
- ✅ 3.4.2: One-to-Many Relationships
- ✅ 3.4.3: Many-to-Many Relationships (Implicit & Explicit)
- ✅ 3.4.4: Self-Relations & Hierarchical Data
- ✅ 3.4.5: Relation Fields & Foreign Keys
- ✅ 3.4.6: Cascade Operations & Referential Actions

### [3.5 Schema Introspection & Best Practices](./3.5-introspection-best-practices/README.md)
- ✅ 3.5.1: Database Introspection (`prisma db pull`)
- ✅ 3.5.2: Schema Validation & Error Handling
- ⏳ 3.5.3: Design Pattern Selection Guidelines
- ⏳ 3.5.4: Performance Considerations in Schema Design
- ⏳ 3.5.5: Migration Strategy Planning

---

## 📝 Module 3 Assessment

### Schema Design Project
**Objective**: Design a comprehensive data model for a real-world application

**Project Requirements**:
1. Create a multi-entity schema with at least 6 models
2. Implement all relationship types (1:1, 1:M, M:M)
3. Use advanced data types and custom attributes
4. Include proper indexing and performance optimization
5. Document schema design decisions
6. Validate schema and generate migration

**Validation Criteria**:
- Schema compiles without errors
- Relationships are properly defined and functional
- Performance considerations are addressed
- Code follows naming conventions and best practices

### Data Modeling Quiz
Test your schema design knowledge:

1. **What is the correct syntax for defining a required field in Prisma?**
   - [ ] A) `name String required`
   - [x] B) `name String`
   - [ ] C) `name String!`
   - [ ] D) `name String @required`

2. **Which attribute creates a many-to-many relationship?**
   - [ ] A) `@relation`
   - [ ] B) `@manyToMany`
   - [x] C) Implicit through relation fields
   - [ ] D) `@connect`

3. **What does the `@@map` attribute do?**
   - [x] A) Maps model name to database table name
   - [ ] B) Maps field to column name
   - [ ] C) Creates database indexes
   - [ ] D) Defines field relationships

### Self-Assessment
- **Schema Design Confidence (1-10)**: ___
- **Relationship Modeling Skills (1-10)**: ___
- **Performance Optimization Understanding (1-10)**: ___
- **Ready for Client Operations?**: Yes / No

---

**Previous:** [02 - Getting Started](../02-getting-started/02-getting-started.md)
**Next:** [04 - Prisma Client](../04-prisma-client/04-prisma-client.md)
