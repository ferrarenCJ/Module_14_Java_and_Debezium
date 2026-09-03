# Mini-Lesson 14.1: Nano Text Editor

## Overview

GNU Nano is a lightweight, command-line text editor commonly used in Linux and Unix environments. Nano is designed to be simple and user-friendly while providing essential text editing capabilities.

Common uses include:

- Creating text files
- Editing configuration files
- Writing scripts
- Modifying source code
- Managing files within containers

---

# Learning Objectives

By the end of this mini-lesson, you should be able to:

- Install Nano in a Linux environment.
- Open existing files.
- Create new files.
- Edit text.
- Save changes.
- Exit Nano safely.
- Search and replace text.
- Cut, copy, and paste content.

---

# Creating a Docker Container

Create a container named `nano_container` using Ubuntu:

```bash
docker run --name nano_container -t -i ubuntu /bin/bash
```

### Parameter Breakdown

| Parameter | Description |
|------------|-------------|
| `docker run` | Creates and starts a container |
| `--name nano_container` | Assigns a container name |
| `-t` | Allocates a terminal |
| `-i` | Runs interactively |
| `ubuntu` | Uses Ubuntu image |
| `/bin/bash` | Opens a Bash shell |

---

# Update Ubuntu Packages

Before installing Nano:

```bash
apt-get update
```

This command updates package information from Ubuntu repositories.

---

# Install Nano

Install Nano with:

```bash
apt-get install nano
```

Verify installation:

```bash
nano --version
```

Example Output:

```text
GNU nano 8.7.1
```

---

# Opening and Creating Files

To create a new file or open an existing file:

```bash
nano HelloWorld.txt
```

If the file exists:

- Nano opens the file.

If the file does not exist:

- Nano creates a new file when saved.

---

# Editing Files

After opening a file:

1. Use arrow keys to navigate.
2. Position the cursor where text should be entered.
3. Begin typing.

Example:

```text
Hello World!!!
```

Unlike Vim, Nano does not require switching between command and insert modes.

---

# Saving Files

To save changes:

```text
Ctrl + O
```

Nano displays:

```text
Write Out
```

Press:

```text
Enter
```

to confirm the filename.

---

# Exiting Nano

To exit:

```text
Ctrl + X
```

If unsaved changes exist:

Nano asks whether changes should be saved.

Options:

```text
Y = Save Changes
N = Discard Changes
```

After making a selection:

```text
Enter
```

to continue.

---

# Searching for Text

To search within a file:

```text
Ctrl + W
```

Enter the search phrase and press:

```text
Enter
```

Nano moves to the first match.

To find the next occurrence:

```text
Alt + W
```

---

# Search and Replace

Launch search and replace:

```text
Ctrl + \
```

Enter:

1. Search text
2. Replacement text

Nano will prompt for each replacement.

Options:

```text
Y = Replace
N = Skip
A = Replace All
```

---

# Selecting Text

Start text selection:

```text
Alt + A
```

Move the cursor using arrow keys.

Selected text becomes highlighted.

Cancel selection:

```text
Ctrl + 6
```

---

# Copying Text

Copy selected text:

```text
Alt + 6
```

Copied text is stored in Nano's internal buffer.

---

# Cutting Text

Cut selected text:

```text
Ctrl + K
```

To cut an entire line:

```text
Ctrl + K
```

while the cursor is on that line.

Multiple lines can be cut by repeatedly pressing:

```text
Ctrl + K
```

---

# Pasting Text

Paste copied or cut content:

```text
Ctrl + U
```

---

# Frequently Used Nano Commands

## File Operations

```text
Ctrl + O   Save File
Ctrl + X   Exit Nano
```

## Navigation

```text
Arrow Keys Move Cursor
Ctrl + W   Search
Alt + W    Find Next
```

## Editing

```text
Ctrl + K   Cut
Ctrl + U   Paste
Alt + 6    Copy
Alt + A    Select Text
```

## Search and Replace

```text
Ctrl + \   Search and Replace
```

---

# Practical Example

Create a file:

```bash
nano HelloWorld.txt
```

Enter:

```text
Hello World!!!
```

Save:

```text
Ctrl + O
Enter
```

Exit:

```text
Ctrl + X
```

Verify file contents:

```bash
cat HelloWorld.txt
```

Output:

```text
Hello World!!!
```

---

# Key Takeaways

- Nano is a beginner-friendly Linux text editor.
- It is commonly installed on Linux servers and containers.
- Nano can create, edit, and manage files entirely from the command line.
- Learning Nano is valuable when working with Docker containers and cloud environments.
- Core commands to remember are:
  - `Ctrl + O` (Save)
  - `Ctrl + X` (Exit)
  - `Ctrl + W` (Search)
  - `Ctrl + K` (Cut)
  - `Ctrl + U` (Paste)

---

# Personal Notes

- Nano is much easier for beginners than Vim.
- Most Docker and Linux labs can be completed using Nano.
- Saving files requires both `Ctrl + O` and `Enter`.
- This tool will be useful throughout the Java, Spring Boot, Docker, and Debezium activities.