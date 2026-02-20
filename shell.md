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
