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
