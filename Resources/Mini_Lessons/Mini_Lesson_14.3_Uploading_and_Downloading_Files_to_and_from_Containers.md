# Mini-Lesson 14.3: Uploading and Downloading Files to and from Containers

## Overview

Working with Docker containers often requires transferring files between a local machine and a container. Docker provides the `docker cp` command to copy files and directories between the host and container file systems.

This capability is useful for:

- Uploading source code
- Loading datasets
- Backing up files
- Restoring data
- Exporting logs
- Moving application outputs

---

# Learning Objectives

By the end of this lesson, you should be able to:

- Copy files from a local machine to a Docker container.
- Copy files from a container to a local machine.
- Copy entire directories.
- Verify successful file transfers.
- Use the `docker cp` command effectively.

---

# Docker Copy Command

The command used to transfer files is:

```bash
docker cp
```

This command supports:

- Host → Container transfers
- Container → Host transfers

---

# Uploading Files to a Container

## File Upload Syntax

```bash
docker cp <source_file_path> <container_id>:<destination_file_path>
```

### Example

```bash
docker cp foo_local_machine.txt ubuntu_container:/home/foo_local_machine.txt
```

Result:

```text
Local Machine
    ↓
foo_local_machine.txt
    ↓
Docker Container
```

---

# Uploading Directories to a Container

## Folder Upload Syntax

```bash
docker cp <source_directory_path/.> <container_id>:<destination_directory_path>
```

### Example

```bash
docker cp project_files/. ubuntu_container:/home/project_files
```

### Important Note

```text
/.
```

copies all files within the directory.

---

# Downloading Files from a Container

## File Download Syntax

```bash
docker cp <container_id>:<source_file_path> <destination_file_path>
```

### Example

```bash
docker cp ubuntu_container:/home/foo_container.txt foo_container.txt
```

Result:

```text
Docker Container
    ↓
foo_container.txt
    ↓
Local Machine
```

---

# Downloading Directories from a Container

## Folder Download Syntax

```bash
docker cp <container_id>:<source_directory_path/.> <destination_directory_path>
```

### Example

```bash
docker cp ubuntu_container:/home/project_files/. .
```

This copies all contents into the current local directory.

---

# Creating a Docker Container

Create a container named:

```bash
ubuntu_container
```

using:

```bash
docker run --name ubuntu_container -dti ubuntu /bin/bash
```

---

# Command Breakdown

```bash
docker run
```

Creates and starts a container.

```bash
--name ubuntu_container
```

Assigns a custom container name.

```bash
-d
```

Runs in detached mode.

```bash
-t
```

Allocates a terminal.

```bash
-i
```

Keeps the container interactive.

```bash
ubuntu
```

Uses the Ubuntu image.

```bash
/bin/bash
```

Starts a Bash shell.

---

# Upload Example

## Step 1: Create Container

```bash
docker run --name ubuntu_container -dti ubuntu /bin/bash
```

---

## Step 2: Open Container CLI

Use Docker Desktop and select:

```text
CLI
```

for the container.

---

## Step 3: Open Local Command Prompt

Navigate to the folder where files are stored.

Example:

```bash
cd Documents
```

---

## Step 4: Create a Local File

Windows:

```cmd
echo local machine > foo_local_machine.txt
```

Linux/macOS:

```bash
echo "local machine" > foo_local_machine.txt
```

---

## Step 5: Upload File

```bash
docker cp foo_local_machine.txt ubuntu_container:/home/foo_local_machine.txt
```

---

## Step 6: Verify Upload

Inside the container:

```bash
cd /home
ls
```

Expected output:

```text
foo_local_machine.txt
```

---

# Download Example

## Step 7: Create File Inside Container

Inside the container:

```bash
echo "hello world" > foo_container.txt
```

Verify:

```bash
cat foo_container.txt
```

Output:

```text
hello world
```

---

## Step 8: Download File

On the local machine:

```bash
docker cp ubuntu_container:/home/foo_container.txt foo_container.txt
```

---

## Step 9: Verify Download

### Windows

```cmd
dir
```

### macOS/Linux

```bash
ls
```

Expected:

```text
foo_container.txt
```

---

# Typical Data Engineering Workflow

## Upload Data

```bash
docker cp sales.csv data_container:/data/
```

---

## Process Data

Inside container:

```bash
python etl.py
```

or

```bash
java Main
```

---

## Download Results

```bash
docker cp data_container:/data/output.csv output.csv
```

---

# Common Docker Commands

## List Running Containers

```bash
docker ps
```

---

## List All Containers

```bash
docker ps -a
```

---

## Open Container Shell

```bash
docker exec -it ubuntu_container bash
```

---

## Copy File to Container

```bash
docker cp localfile.txt ubuntu_container:/home/
```

---

## Copy File from Container

```bash
docker cp ubuntu_container:/home/file.txt .
```

---

# Key Terms

## Host Machine

The computer running Docker.

---

## Container

An isolated environment containing applications and dependencies.

---

## Docker

A platform used to create and run containers.

---

## docker cp

A command used to transfer files between a host and a container.

---

## CLI

Command Line Interface used to interact with the operating system or container.

---

# Key Takeaways

- Containers have isolated file systems.
- Files do not automatically exist inside containers.
- The `docker cp` command enables file transfers between the host and container.
- Files and directories can be transferred in both directions.
- The `/.` notation copies all files within a directory.
- File transfers are commonly used when developing applications and data engineering pipelines.
- Understanding file movement is essential for working with Docker, Spring Boot, MySQL, and Debezium.

---

# Personal Notes

- `docker cp` is one of the most useful Docker commands for development and troubleshooting.
- Uploading and downloading files allows quick testing without using Docker volumes.
- Data engineers frequently move CSV, JSON, log, and configuration files in and out of containers.
- This knowledge will be useful for upcoming activities involving Java applications, MySQL, and Debezium.