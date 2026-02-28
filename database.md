## Truncate Prisma Migrations Table

```bash
TRUNCATE _prisma_migrations;
```

#### This SQL command deletes all rows from the internal table Prisma uses to track which migrations have been applied to your database, effectively "forgetting" the migration history without deleting the table structure itself.

#### Flags Breakdown:

- **`TRUNCATE`** : A Data Definition Language (DDL) operation that quickly removes all records from a table. It is typically faster than **`DELETE`** because it doesn't log individual row deletions.

- **`_prisma_migrations`** : The specific metadata table created and managed by Prisma Migrate to keep track of which migration files have been successfully executed.

---
