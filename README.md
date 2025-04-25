# linux-pr
# Intro to Linux Shell Scripting

This repository introduces the basics of Linux shell scripting. A shell script is a plain text file containing a sequence of commands. When executed, it runs the commands listed from top to bottom, line by line, just as if you had typed them directly into the terminal. This makes shell scripting a powerful tool for automating repetitive tasks performed via the command line.

---

## Prerequisites: Text Editor

To create and execute shell scripts, a text editor is required. If you already have a preferred text editor installed, you're good to go. Otherwise, consider using one of the following:

- **GUI Editors**: `gvim`, `gedit`, etc.
- **Terminal-based Editors**: `vim`, `nano`

Some Linux distributions come with `nano` pre-installed. If not, install it using the appropriate command for your system:

- **RedHat-based systems**:
  ```bash
  sudo yum install -y nano
  ```
- **Debian-based systems**:
  ```bash
  sudo apt-get install -y nano
  ```

In this tutorial, we will use `nano` for all examples.

---

## Creating Your First Shell Script

1. **Create a file using `nano`:**
   ```bash
   nano day1.sh
   ```
   The `.sh` extension is conventional but not required. What matters most is having the appropriate execution permissions.

2. **Check file permissions** using:
   ```bash
   ls -l
   ```
   Example output:
   ```
   -rw-r--r-- 1 user user 0 Apr 16 15:14 day1.sh
   ```

3. **Understanding file permissions:**

   - `-` indicates a regular file (use `d` for directories).
   - The permission string `rw-r--r--` breaks down as:
     - `rwx`: Owner's permissions (read, write, execute)
     - `r-x`: Group's permissions
     - `r-x`: Others' permissions

4. **Add execute permissions** using:
   ```bash
   chmod +x day1.sh
   ```
   Rechecking with `ls -l` should show:
   ```
   -rwxr-xr-x 1 user user 0 Apr 16 15:17 day1.sh
   ```

---

## Writing and Executing the Script

1. Open the file again using:
   ```bash
   nano day1.sh
   ```

2. Add the following content:
   ```bash
   #!/bin/bash
   echo "You don't need to be great to start something, but you need to start to be great."
   ```

3. Save and exit:
   - Press `Ctrl + O` to write the file
   - Press `Enter` to confirm
   - Press `Ctrl + X` to exit

4. **Run the script**:
   ```bash
   ./day1.sh
   ```

   Output:
   ```
   You don't need to be great to start something, but you need to start to be great.
   ```

---

## Script Header: `#!/bin/bash`

The line `#!/bin/bash` is called a **shebang**. It tells the operating system to use the Bash shell to interpret the script.

---

## Understanding Commands: Built-ins vs External

To check the type of a command:
```bash
type <command>
```

Example:
```bash
type echo
# Output: echo is a shell builtin
```

---

## Using Variables in Shell Scripts

Let's add variables to a script.

### Example:
```bash
#!/bin/bash
SKILL="Shell Scripting"
echo "I am best at ${SKILL}, and trying to learn more about ${SKILL}."
```

### Output:
```
I am best at Shell Scripting, and trying to learn more about Shell Scripting.
```

### Rules for Variable Naming:
1. Variable names may include letters, digits, and underscores.
2. They must **start** with a letter or an underscore.
3. It's common practice to use uppercase for variable names.

#### Valid examples:
- `SKILL`, `Skill`, `_Skill`, `skill`

#### Invalid examples:
- `0Skill`, `-SKILL`, `@skill`, `S@kill`

---

## Writing Longer Scripts

You can write longer, more functional scripts by incorporating comments and system commands.

### Example:
```bash
#!/bin/bash

# This script displays system information.

echo "Starting the sysinfo script."

# Display system hostname
hostname

# Display current date and time
date

# Display kernel release and architecture
uname -r
uname -m

# Display disk usage
df -h

echo "Stopping the code."
```

---

## Decision-Making in Shell Scripts

Automation often requires logic. `if` statements allow your scripts to make decisions.

### Example: Check for Root Privileges
```bash
#!/bin/bash

# Display the UID of the user
echo "Your UID is ${UID}"

# Check if the user is root
if [[ "${UID}" -eq 0 ]]
then
    echo "You are root."
else
    echo "You are not root."
fi
```

### Practical Example: Software Installation
```bash
#!/bin/bash

echo "Your UID is ${UID}"

if [[ "${UID}" -eq 0 ]]
then
    echo "Installing software..."
    # Place installation commands here
else
    echo "You do not have the permission to install the software."
fi
```

---

## Summary

This repository offers a foundational guide to writing, executing, and understanding basic shell scripts. As you progress, you’ll learn to automate more complex tasks using conditionals, loops, and functions.

Happy scripting!

