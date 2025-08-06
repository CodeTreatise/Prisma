# Module 2: Getting Started (First Steps)

## 📋 Module Overview
- **Duration**: 2-3 hours
- **Prerequisites**: 
  - Completed Module 1: Foundations
  - Node.js 18+ installed
  - Basic TypeScript knowledge
  - Code editor setup (VS Code recommended)
- **Learning Objectives**: 
  - Install and configure Prisma in a new project
  - Create your first Prisma schema and database connection
  - Execute your first migration and generate Prisma Client
  - Perform basic CRUD operations using Prisma
  - Master essential CLI commands for daily development
- **Assessment Type**: Hands-on Project + CLI Quiz
- **Difficulty Level**: Beginner to Intermediate
- **Next Module**: [03-prisma-schema.md](../03-prisma-schema/03-prisma-schema.md)

---

## 🎯 What You'll Learn

By the end of this module, you will:
- ✅ Have Prisma fully installed and configured in a TypeScript project
- ✅ Understand database connection strings and provider configuration
- ✅ Create and run your first database migration
- ✅ Generate and use Prisma Client for database operations
- ✅ Perform basic CRUD operations with type safety
- ✅ Navigate Prisma CLI commands confidently
- ✅ Use Prisma Studio for database exploration

---

## 📚 Table of Contents

### [2.1 Installation & Setup](./2.1-installation-setup/README.md)
- ✅ 2.1.1: Installing Prisma CLI & Client
- ✅ 2.1.2: Project Initialization with `prisma init`
- ✅ 2.1.3: Package.json Configuration & Scripts
- ✅ 2.1.4: Environment Variables & .env Setup
- ✅ 2.1.5: TypeScript Configuration for Prisma

### [2.2 First Prisma Project](./2.2-first-prisma-project/README.md)
- ✅ 2.2.1: Creating Your First Schema
- ✅ 2.2.2: Database Connection String Configuration
- ✅ 2.2.3: Running First Migration with `prisma migrate dev`
- ✅ 2.2.4: Generating Prisma Client with `prisma generate`
- ✅ 2.2.5: First Query & CRUD Operations

### [2.3 Database Connection](./2.3-database-connection/README.md)
- ✅ 2.3.1: Connection String Formats & Parameters
- ✅ 2.3.2: Database Providers (PostgreSQL, MySQL, SQLite, MongoDB)
- ✅ 2.3.3: Connection Pooling Basics & Configuration
- ✅ 2.3.4: SSL Configuration & Security
- ✅ 2.3.5: Environment-Specific Connection Management

### [2.4 Prisma CLI Basics](./2.4-prisma-cli-basics/README.md)
- ✅ 2.4.1: Essential CLI Commands Overview
- ✅ 2.4.2: Help & Documentation (`prisma --help`)
- ✅ 2.4.3: Studio for Database Exploration (`prisma studio`)
- ✅ 2.4.4: Format & Validation (`prisma format`, `prisma validate`)
- ✅ 2.4.5: Custom Scripts & Automation
- 🎓 2.4.6: Migration Commands Deep Dive (Advanced)

---

## 📝 Module 2 Assessment

### Hands-on Project
**Objective**: Build a complete Prisma setup from scratch

**Project Requirements**:
1. ✅ Initialize a new TypeScript project with Prisma
2. ✅ Configure database connection (PostgreSQL recommended)
3. ✅ Create a schema with at least 2 related models
4. ✅ Run migrations and generate client
5. ✅ Implement CRUD operations for both models
6. ✅ Use Prisma Studio to explore data

**Validation**: 
- Project runs without errors
- Database contains expected tables and data
- CRUD operations work correctly with type safety

### CLI Mastery Quiz
Test your command-line proficiency:

1. **Which command initializes a new Prisma project?**
   - [ ] A) `prisma create`
   - [x] B) `prisma init`
   - [ ] C) `prisma new`
   - [ ] D) `prisma setup`

2. **What does `prisma migrate dev` do?**
   - [x] A) Creates and applies migrations for development
   - [ ] B) Only creates migration files
   - [ ] C) Deploys to production
   - [ ] D) Resets the database

3. **Which command opens the database browser?**
   - [ ] A) `prisma db`
   - [ ] B) `prisma browser`
   - [x] C) `prisma studio`
   - [ ] D) `prisma explore`

### Self-Assessment
- **Confidence Level (1-10)**: ___
- **Time Spent**: ___ hours
- **Topics to Review**: _______________
- **Ready for Next Module?**: Yes / No

---

**Previous:** [01 - Foundations](../01-foundations/01-foundations.md)
**Next:** [03 - Prisma Schema](../03-prisma-schema/03-prisma-schema.md)