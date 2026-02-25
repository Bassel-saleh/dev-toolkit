### Docker Compose (PostgreSQL)

```shell
docker compose up postgres -d
```

#### This command is used to build, create, and start the PostgreSQL container service in the background as defined in your configuration file.

#### Flags Breakdown:

- The command used to create and start containers defined in your **`docker-compose.yml`** file.
- **`postgres`** : Specifies that only the service named postgres (as defined in your YAML file) should be started, ignoring other services.
- **`-d`** : Runs the container in detached mode, meaning it runs in the background so it doesn't occupy your terminal. **Remove it if detached mode is unnecessary** .

---

### PostgreSQL CLI (psql)

```shell
docker exec -it docker_continer_name psql -U user_name -d database_name
```

#### This command is used to open PostgreSQL CLI in you terminal.

#### Flags Breakdown:

- **`docker exec -it`** : Runs the command in interactive mode with a TTY (so you can type and see output).
- **`docker_continer_name`** : The name of your specific Docker container.
- **`psql`** is the interactive terminal-based front-end for managing PostgreSQL databases.
- **`-U`** : specifies the user.
- **`user_name`** : The name of your specific container user
- **`-d`** : name of the database you are targeting inside the container.
- **`database_name`** : The name of your specific database inside the container.
- **`psql`** : The command-line utility used to interact with PostgreSQL. opens postgresql command shell .

---

### PostgreSQL Database Backup (via Docker)

```shell
docker exec -t <container_name> pg_dump -U <username> -d <database_name> > backup.sql
```

#### This command runs the **`pg_dump`** utility inside a running Docker container to create a SQL export of a specific database and saves it as a file on your local host machine.

#### Flags Breakdown:

- **`docker exec`** : Executes a command in a running container.

- **`-t`** : Allocates a pseudo-TTY (Terminal) to facilitate the data stream.

- **`<container_name>`** : The name of your specific PostgreSQL Docker container.

- **`pg_dump`** : The PostgreSQL utility used for backing up a database by extracting it into a script file.

- **`-U`** : Specifies the database user.

- **`<username>`** : The name of your specific database user (e.g., **`postgres`**).

- **`-d`** : Specifies the name of the database to be dumped.

- **`<database_name>`** : The name of the specific database you want to backup.

- **`>`** : The redirection operator that sends the output of the command to a file instead of displaying it in the terminal.

- **`backup.sql`** : The name of the resulting file on your local machine where the data will be stored.

---

### PostgreSQL Database Restore (via Docker) (For \*.sql Files)

```shell
cat backup.sql | docker exec -i <container_name> psql -U <username> -d <database_name>
```

#### This command reads a SQL backup file from your local machine and pipes its contents into a running PostgreSQL Docker container to restore or populate a specific database.

#### Flags Breakdown:

- **`cat backup.sql`** : Reads the content of your local SQL backup file and outputs it to the terminal's standard output.

- **`|`** : The pipe operator, which takes the output from the left command (cat) and sends it as input to the right command (docker exec).

- **`docker exec`** : Executes a command inside a running Docker container.

- **`-i`** : Interactive mode – keeps standard input (STDIN) open, which is necessary to receive the piped SQL data.

- **`<container_name>`** : The name of your target PostgreSQL Docker container.

- **`psql`** : The PostgreSQL interactive terminal utility used to execute SQL commands.

- **`-U`** : Specifies the database user.

- **`<username>`** : The name of the database user (e.g., **`postgres`**).

- **`-d`** : Specifies the target database where the data will be restored.

- **`<database_name>`** : The name of the specific database you are targeting.

---

### PostgreSQL Custom Format Backup (via Docker)

```bash
docker exec -t <container_name> pg_dump -U <username> -Fc <database_name> > backup.dump
```

#### This command creates a compressed, custom-format backup of a PostgreSQL database from within a Docker container and saves it to a local file. This format is more flexible and efficient than plain SQL text.

#### Flags Breakdown:

- **`docker exec`** : Executes a command in a running container.

- **`-t`** : Allocates a pseudo-TTY to facilitate the data stream.

- **`<container_name>`** : The name of your specific PostgreSQL Docker container.

- **`pg_dump`** : The PostgreSQL utility used for extracting a database into a file for backup.

- **`-U`** : Specifies the database user.

- **`<username>`** : The name of the database user (e.g., **`postgres`**).

- **`-Fc`** : Selects the custom format output. This is a binary, compressed format that allows for faster restores and the ability to reorder or exclude items during restoration.

- **`<database_name>`** : The name of the specific database you want to backup.

- **`>`** : The redirection operator that sends the output to a file on your local host machine.

- **`backup.dump`** : The name of the output file where the compressed backup data will be stored.

---

### PostgreSQL Custom Format Restore (via Docker)

```shell
docker exec -i <container_name> pg_restore -U <username> -d <database_name> --clean --no-owner < backup.dump
```

#### This command restores a compressed, custom-format PostgreSQL backup file (**`.dump`**) into a database running inside a Docker container, cleaning existing objects first to ensure a fresh state.

#### Flags Breakdown:

- **`docker exec -i`** : Executes the command in the container and keeps standard input (STDIN) open, allowing it to receive the backup data.

- **`<container_name>`** : The name of the target PostgreSQL Docker container.

- **`pg_restore`** : The utility specifically designed to restore backups created by **`pg_dump`** in non-plain-text formats (like **`-Fc`**).

- **`-U <username>`** : Specifies the database user to connect as.

- **`-d <database_name>`** : Specifies the target database where the data will be restored.

- **`--clean`** : Tells the utility to drop (clean) existing database objects before recreating them, preventing "already exists" errors.

- **`--no-owner`** : Skips commands to set ownership of objects to the original user, which is useful when restoring to a different environment.

- **`< backup.dump`** : The redirection operator that feeds the content of your local backup file into the restore command.

---

### PostgreSQL Database Deletion (via Docker)

```shell
docker exec -it <container_name> dropdb -U <username> <database_name>
```

#### This command allows you to permanently delete an existing PostgreSQL database from within a running Docker container using the **`dropdb`** utility.

#### Flags Breakdown:

- **`docker exec -it`** : Runs the command in interactive mode with a TTY, allowing you to interact with the container's shell if prompted (for example, if a password is required).

- **`<container_name>`** : The name of your running PostgreSQL Docker container.

- **`dropdb`** : A command-line executable used to remove an existing PostgreSQL database.

- **`-U <username>`** : Specifies the database user to connect as to perform the deletion (usually requires superuser or database owner privileges).

- **`<database_name>`** : The name of the specific database you want to permanently remove.

---

### Stop Docker Container

```shell
docker stop <container_name>
```

#### This command gracefully shuts down a running container by sending a SIGTERM signal, giving the processes inside time to save data and terminate properly.

#### Flags Breakdown:

- **`docker stop`** : The command used to halt the execution of one or more running containers.

- **`<container_name>`** : The specific name or unique ID of the container you want to stop.

---

### Remove Docker Container

```shell
docker rm <container_name>
```

#### This command permanently removes one or more stopped containers from your host machine, freeing up system resources.

#### Flags Breakdown:

- **`docker rm`** : The command used to delete a container that is no longer running.

- **`<container_name>`** : The specific name or unique ID of the container you wish to remove.

---

### List Docker Volumes

```shell
docker volume ls
```

#### This command provides a list of all the volumes currently managed by Docker on your host machine, showing their driver and unique volume name.

#### Flags Breakdown:

- **`docker volume`** : The parent command used to manage persistent data storage volumes.

- **`ls`** : Short for "list"—it displays a table of all available volumes.

---

### Remove Docker Volume

```shell
docker volume rm <volume_name>
```

#### This command permanently deletes one or more specified Docker volumes from your host machine, which is useful for cleaning up persistent data that is no longer needed.

#### Flags Breakdown:

- **`docker volume`** : The parent command used to manage persistent data storage in Docker.

- **`rm`** : The remove command used to delete specific volumes.

- **`<volume_name>`** : The unique name of the volume you want to delete.

#### Deleting a volume is permanent. All tables, rows, and configurations stored in that volume will be lost.
