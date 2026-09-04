# Coding Activity 14.1: Uploading and Downloading Files to and from Containers

## Activity Information

### Module

Module 14: Java and Debezium

### Activity

Required Coding Activity 14.1: Uploading and Downloading Files to and from Containers

### Learning Outcome

- Upload and download files to and from containers.

---

# Objective

Learn how to move files and folders between a Docker container and a local machine using the `docker cp` command.

This activity demonstrates how containerized environments maintain their own isolated file systems and how data can be transferred between a host machine and a Docker container.

---

# Purpose

Modern software applications, data engineering pipelines, and cloud-native systems frequently run inside containers.

Since containers use isolated file systems, engineers often need to:

- Upload files into containers
- Download files from containers
- Transfer datasets
- Export logs
- Move application outputs
- Manage configuration files

This activity provides hands-on experience with these tasks.

---

# Key Concepts

## Docker Container

A Docker container is an isolated environment that packages:

- Application code
- Runtime dependencies
- System libraries
- Configuration files

Containers allow applications to run consistently across different environments.

---

## Host Machine

The host machine is the computer running Docker.

Examples:

- Windows
- macOS
- Linux

---

## Docker Copy Command

The `docker cp` command transfers files and folders between:

```text
Host Machine
      ↕
Docker Container
```

Syntax:

```bash
docker cp source destination
```

---

# Activity Tasks

## Task 1: Create Docker Container

Created a container named:

```text
ubuntu_container
```

Command:

```bash
docker run --name ubuntu_container -dti ubuntu /bin/bash
```

Purpose:

- Create a running Ubuntu container.
- Provide an isolated environment for file management.

---

## Task 2: Open Container CLI

Accessed the container command-line interface through Docker Desktop.

Prompt example:

```bash
root@container:/#
```

Purpose:

- Interact directly with the container.
- Create and manage files inside the container.

---

## Task 3: Create Folder and File

Commands:

```bash
cd /home

mkdir container_activity_14.1

touch container_activity_14.1/container1.txt
```

Folder structure:

```text
/home
└── container_activity_14.1
    └── container1.txt
```

Purpose:

- Create a directory within the container.
- Create a file to demonstrate file transfer.

---

## Task 4: Add Content

Command:

```bash
echo "Hello World" > container_activity_14.1/container1.txt
```

Verification:

```bash
cat container_activity_14.1/container1.txt
```

Output:

```text
Hello World
```

Purpose:

- Create actual file content.
- Verify that contents are preserved during transfer.

---

## Task 5: Create Local Directory

Commands:

```cmd
mkdir local_activity_14.1
```

Navigate:

```cmd
cd local_activity_14.1
```

Purpose:

- Create a destination location on the host machine.
- Receive files copied from the container.

---

## Task 6: Copy Folder from Container

Command:

```bash
docker cp ubuntu_container:/home/container_activity_14.1 .
```

Result:

```text
container_activity_14.1
```

successfully copied to:

```text
local_activity_14.1
```

Purpose:

- Demonstrate downloading files from a container.
- Practice using the `docker cp` command.

---

## Task 7: Validate File Transfer

Commands:

```cmd
cd container_activity_14.1

type container1.txt
```

Output:

```text
Hello World
```

Purpose:

- Confirm successful transfer.
- Verify file integrity.
- Ensure file contents remained unchanged.

---

# Commands Used

## Create Container

```bash
docker run --name ubuntu_container -dti ubuntu /bin/bash
```

---

## Create Folder

```bash
mkdir container_activity_14.1
```

---

## Create File

```bash
touch container_activity_14.1/container1.txt
```

---

## Add Content

```bash
echo "Hello World" > container_activity_14.1/container1.txt
```

---

## Display File Contents

```bash
cat container_activity_14.1/container1.txt
```

---

## Create Local Folder

```cmd
mkdir local_activity_14.1
```

---

## Change Directory

```cmd
cd local_activity_14.1
```

---

## Copy Folder from Container

```bash
docker cp ubuntu_container:/home/container_activity_14.1 .
```

---

## Verify Contents

```cmd
type container1.txt
```

---

# Folder Structures

## Inside Container

```text
/home
└── container_activity_14.1
    └── container1.txt
```

### Contents

```text
Hello World
```

---

## Local Machine After Copy

```text
local_activity_14.1
└── container_activity_14.1
    └── container1.txt
```

### Contents

```text
Hello World
```

---

# Data Engineering Relevance

As a data engineer, file transfers between containers and host systems are extremely common.

Examples include:

### Uploading Data

```text
CSV
JSON
Parquet
```

files into processing containers.

---

### Downloading Results

Moving output data, reports, or transformed datasets back to a local machine.

---

### Collecting Logs

Exporting application logs from containers for troubleshooting.

---

### Moving Configurations

Managing application settings and configuration files.

---

### ETL Workflows

Loading source data into containerized data processing pipelines.

---

# Lessons Learned

- Containers maintain independent file systems.
- Files are not automatically shared between a host and a container.
- The `docker cp` command enables file transfers in both directions.
- File transfers should always be validated after completion.
- Docker containers simplify application deployment but require careful file management.
- Understanding file movement is a foundational Docker skill that supports future work with data pipelines, cloud platforms, and container orchestration systems.

---

# Challenges Encountered

- Ensuring commands were executed in the correct environment:
  - Container terminal
  - Local machine terminal
- Understanding the distinction between host and container file systems.
- Verifying that directory structures remained intact after transfer.

---

# Key Takeaways

- Docker containers are isolated environments.
- `docker cp` is used to move files and directories between a container and a host system.
- Files should be validated after transfer.
- Container file management is a critical skill for modern software development and data engineering.
- Understanding Docker file transfers provides a foundation for future work with Kubernetes, cloud services, and data platforms.

---

# Completion Status

```text
✅ Completed
```