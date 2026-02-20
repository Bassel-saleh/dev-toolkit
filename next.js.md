## Prisma Database Push

```bash
npx prisma db push
```

#### This command synchronizes the state of your Prisma schema file directly with your database schema without creating or using migration files.

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

### This command executes the seeding script defined in your project to populate your database with initial or test data.

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

- **`npx`** : Executes the Prisma package from your local **`node_modules`** without needing a global installation.
- **`prisma`** : The command-line interface for the Prisma ORM toolkit.
- **`studio`** : Starts the Prisma Studio server and opens the browser interface for direct database interaction.
