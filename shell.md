## Bash Shebang Line

```bash
#!/bin/bash
```

#### This "shebang" is placed at the very first line of a script file to inform the operating system that the file should be executed using the Bash shell.

- **`#!`** : The shebang (or hashbang) character sequence that indicates the start of a script and specifies the path to the interpreter.

- **`/bin/bash`** : The absolute path to the Bash (Bourne Again SHell) executable on most Unix-like systems. It tells the system to use the Bash shell specifically, rather than the default system shell (**`/bin/sh`**).

---

## Bash Shebang (Environment-Independent)

```bash
#!/usr/bin/env bash
```

#### This "shebang" is placed at the very top of a script to instruct the operating system to locate and use the Bash shell interpreter through the system's environment settings.

- **`#!`** : The shebang (or hashbang) sequence that tells the kernel to use the interpreter specified on the rest of the line to execute the script.

- **`/usr/bin/env`** : A system utility that searches for the specified command in the user's current PATH. This makes the script more portable because it doesn't rely on Bash being in a fixed location (like **`/bin/bash`**).

- **`bash`** : Specifies the Bourne Again SHell as the interpreter to be found and used for executing the code.

---

## Recursive Search

```bash
grep -rin "word" .
```

#### To search for a specific word in all files within the current directory and all subdirectories.

#### Flags Breakdown:

- **`-r`** : **Recursive** – search through all subdirectories.

- **`-i`** : **Ignore Case** – matches both uppercase and lowercase.

- **`-n`** : **Line Number** – shows exactly which line the match is on.

---

## Secure Copy: Remote to Local

```bash
scp username@remote_host:/path/to/remote/file /local/destination/path
```

#### This command uses the Secure Copy Protocol (SCP) to safely transfer a file from a remote server to your local machine over an encrypted SSH connection.

#### Flags Breakdown:

- **`scp`** : The command-line utility used to securely copy files between hosts on a network.

- **`username`** : Your login name on the remote server.

- **`remote_host`** : The IP address or domain name of the server you are connecting to.

- **`:/path/to/remote/file`** : The absolute or relative path to the specific file on the remote server that you want to copy.

- **`/local/destination/path`** : The location on your local computer where the file will be saved.

---

## Create Directory (with Parent Flag)

```bash
mkdir -p ~/new_folder
```

#### This command creates a new directory named backups in your home folder. The -p flag ensures that the command succeeds even if the folder already exists and creates any necessary parent folders in the path.

#### Flags Breakdown:

- **`mkdir`** : Short for "make directory," the standard command used to create new folders in a Linux/Unix-like environment.

- **`-p`** : The parents flag. It allows the command to create a full path of directories (e.g., **`mkdir -p project/src/utils`**) and prevents an error message if the directory already exists.

---

## SSH Persistent Remote Port Forwarding

```bash
ssh -N -f -R [Remote_Listening_Port]:[Local_Database_Host]:[Local_Database_Port] [User]@[Remote_Server_IP]
```

#### This command establishes a backgrounded, non-interactive SSH tunnel that maps a port on a remote server back to your local database, allowing the remote machine to access your local data as if it were running locally.

#### Flags Breakdown:

- **`ssh`** : The Secure Shell utility used for encrypted communication.

- **`-N`** : Tells SSH not to execute a remote command. This is useful when you only want to set up a port forwarding tunnel and don't need a shell prompt.

- **`-f`** : Requests SSH to go to the background just before command execution. This lets the tunnel run silently in the background of your terminal.

- **`-R`** : Initiates Remote Port Forwarding. It maps a port on the remote server to a destination accessible from your local machine.

- **`[Remote_Listening_Port]`** : The port number on the remote server that will "listen" for incoming connections (e.g., **`5432`**).

- **`[Local_Database_Host]`** : The address of your database relative to your local machine (usually **`localhost`** or **`127.0.0.1`**).

- **`[Local_Database_Port]`** : The port your local database is actually running on (e.g., **`5432`** for PostgreSQL).

- **`[User]@[Remote_Server_IP]`** : The login credentials and address for the remote server you are connecting to.
