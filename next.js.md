## Prisma Database Push

```bash
npx prisma db push
```

#### This command synchronizes the state of your Prisma schema file directly with your database schema without creating or using migration files.

#### Flags Breakdown:

- It calculates the difference between your **`schema.prisma`** file and the actual database.
- It applies the necessary changes (creating tables, adding columns) directly to the database to match your schema.

- **`npx`** : Executes the Prisma package from your local **`node_modules`** without needing a global installation.
- **`prisma`** : The command-line interface for the Prisma ORM toolkit.
- **`db push`** : Pushes the current state of your Prisma schema file to the database. It is primarily used for rapid prototyping where a migration history is not required.

---

## Prisma Database Seed

```bash
npx prisma db seed
```

#### This command executes the seeding script defined in your project to populate your database with initial or test data.

#### Flags Breakdown:

- **`npx`** : Runs the Prisma package from your local.

- **`node_modules`** without requiring a global installation.

- **`prisma`** : The command-line interface for the Prisma ORM toolkit.

- **`db seed`** : Triggers the specific seed command or script defined in the **`prisma`** section of your **`package.json`** file to insert records into your database.

---

## Prisma Studio GUI

```bash
npx prisma studio
```

#### This command launches an interactive, visual editor for your database in your default web browser, allowing you to view and edit data without writing SQL.

#### Flags Breakdown:

- **`npx`** : Executes the Prisma package from your local **`node_modules`** without needing a global installation.
- **`prisma`** : The command-line interface for the Prisma ORM toolkit.
- **`studio`** : Starts the Prisma Studio server and opens the browser interface for direct database interaction.

---

## Prisma Development Migration

```bash
npx prisma migrate dev --name describe_your_database_changes
```

#### This command creates a new migration file based on changes made to your Prisma schema, applies that migration to your development database, and regenerates the Prisma Client.

#### Flags Breakdown:

- **`npx`** : Executes the Prisma package from your local **`node_modules`** without requiring a global installation.

- **`prisma`** : The command-line interface for the Prisma ORM toolkit.

- **`migrate dev`** : Specifically used in development to track schema changes, create migration files, and update the database.

- **`--name`** : A flag used to provide a descriptive title for the migration.

- **`describe_your_database_changes`** : A placeholder for your custom description (e.g., **`init`** or **`add-user-table`**), which becomes part of the migration folder name.

---

## Prisma Client Generation

```bash
npx prisma generate
```

#### This command reads your Prisma schema file and generates a tailored Prisma Client library, which provides type-safe database access for your specific data models.

#### Flags Breakdown:

- **`npx`** : Runs the Prisma package from your local **`node_modules`** without requiring a global installation.

- **`prisma`** : The command-line interface for the Prisma ORM toolkit.

- **`generate`** : Triggers the generation process. It looks at the **`generator`** block in your **`schema.prisma`** file (usually **`provider = "prisma-client-js"`**) and creates the necessary code in **`node_modules/.prisma/client`**.

---

## Prisma Migration Status

```bash
npx prisma migrate status
```

#### This command inspects the current state of your database and compares it with your local migration history to determine if your schema is in sync or if any migrations are pending or failed.

#### Flags Breakdown:

- **`npx`** : Executes the Prisma package from your local **`node_modules`** without requiring a global installation.

- **`prisma`** : The command-line interface for the Prisma ORM toolkit.

- **`migrate status`** : Queries the **`_prisma_migrations`** table in your database and checks the **`./prisma/migrations`** folder to report on the "health" and progress of your migrations.

---

## Prisma Migration Deployment

```bash
npx prisma migrate deploy
```

#### This command applies any pending migrations to your database. It is specifically designed for production and staging environments because it does not depend on the shadow database and will never reset the database.

#### Flags Breakdown:

- **`npx`** : Executes the Prisma package from your local **`node_modules`** without needing a global installation.

- **`prisma`** : The command-line interface for the Prisma ORM toolkit.

- **`migrate deploy`** : Compares the migrations already applied in the **`_prisma_migrations`** table with the migration files in your **`prisma/migrations`** folder and executes any that are missing.

---

## Prisma Migrate Resolve (Mark as Applied)

```bash
npx prisma migrate resolve --applied 20260227190000_init
```

#### This command allows you to manually record a failed or skipped migration as "applied" in the **`_prisma_migrations`** table without actually running the SQL script against your database.

#### Flags Breakdown:

- **`npx`** : Executes the Prisma package from your local **`node_modules`** without needing a global installation.

- **`prisma`** : The command-line interface for the Prisma ORM toolkit.

- **`migrate resolve`** : A specialized command used to fix a "failed" state in your migration history by manually changing the status of a specific migration.

- **`--applied`** : A flag that tells Prisma to record the specified migration as successfully completed in the database's internal tracking table.

- **`20260227190000_init`** : The unique name of the migration folder you want to mark as applied. It consists of a timestamp followed by the name you gave the migration.

---

## PostgreSQL Grant Superuser Privileges

```bash
ALTER USER "User" WITH SUPERUSER;
```

#### This SQL command modifies an existing database user's attributes to grant them SUPERUSER status, giving them full control over the entire PostgreSQL instance, including the ability to bypass all permission checks.

#### Flags Breakdown:

- **`ALTER USER`** : The Data Control Language (DCL) command used to change the attributes of an existing database role or user.

- **`"User"`** : The specific name of the database user you are modifying.
  - Note: If the username is a reserved keyword or case-sensitive (like **`User`**), it should be enclosed in double quotes.

- **`WITH`** : An optional keyword used to introduce the attribute being changed.

- **`SUPERUSER`** : The highest level of privilege in PostgreSQL. A superuser can create databases, manage other roles, and perform any operation within the database system regardless of ownership.

---
