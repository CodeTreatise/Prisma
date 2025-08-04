# 5. PRISMA MIGRATE (Schema Evolution)

### 5.1 Migration Concepts

- **5.1.1** What Are Migrations & Why They're Important
- **5.1.2** Migration History & State Tracking
- **5.1.3** Shadow Database Concept & Purpose
- **5.1.4** Schema Drift Detection & Prevention
- **5.1.5** Migration vs Introspection Workflows

### 5.2 Development Workflow

- **5.2.1** Creating Migrations (`prisma migrate dev`)
- **5.2.2** Migration Naming Conventions & Organization
- **5.2.3** Reviewing Migration Files & SQL
- **5.2.4** Iterative Development & Schema Changes
- **5.2.5** Reset & Seed Operations (`prisma migrate reset`)

### 5.3 Production Deployment

- **5.3.1** Migration Deployment (`prisma migrate deploy`)
- **5.3.2** Zero-Downtime Migration Strategies
- **5.3.3** Rollback Strategies & Recovery
- **5.3.4** Environment Promotion Workflows
- **5.3.5** CI/CD Integration & Automation

### 5.4 Schema Evolution

- **5.4.1** Breaking vs Non-breaking Changes
- **5.4.2** Data Transformation During Migrations
- **5.4.3** Gradual Schema Changes & Feature Flags
- **5.4.4** Backward Compatibility Strategies
- **5.4.5** Database Versioning & Release Management

### 5.5 Migration Troubleshooting

- **5.5.1** Common Migration Errors (P3006, P3009, P3014)
- **5.5.2** Shadow Database Issues & Resolution
- **5.5.3** Migration Conflicts & History Corruption
- **5.5.4** Recovery Strategies (Baseline Migration)
- **5.5.5** Cross-Platform Migration Challenges
- **5.5.6** Manual Intervention & Custom Scripts

---

**Previous:** [04 - Prisma Client](./04-prisma-client.md)
**Next:** [06 - Advanced Querying](./06-advanced-querying.md)