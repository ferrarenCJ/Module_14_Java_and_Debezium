# Coding Activity 14.1: Uploading and Downloading Files to and from Containers

## Objective

The objective of this activity is to learn how to transfer files and folders between a Docker container and a local machine using the `docker cp` command. This activity demonstrates how Docker containers maintain separate file systems and how data can be copied, managed, and validated between a host computer and a containerized environment.

---

## Purpose

The purpose of this activity is to develop hands-on experience with Docker file management. By creating files inside a container, copying them to a local machine, and verifying the contents, students gain practical knowledge of container operations that are commonly used in software development, DevOps, cloud computing, and data engineering workflows.

---

## Learning Outcome

- Upload and download files to and from containers.

---

## Activity Summary

In this activity:

1. Created a Docker container named `ubuntu_container`.
2. Opened the container command-line interface.
3. Created a folder named `container_activity_14.1`.
4. Created the file `container1.txt`.
5. Added the text `Hello World` to the file.
6. Created a local folder named `local_activity_14.1`.
7. Copied the folder from the container to the local machine using `docker cp`.
8. Validated that the file copied successfully.

---

## Steps Performed

### Step 1: Create Docker Container

```bash
docker run --name ubuntu_container -dti ubuntu /bin/bash
```

### Step 2: Open Container CLI

Open Docker Desktop and access the container terminal.

---

### Step 3: Create Folder and File

```bash
cd /home

mkdir container_activity_14.1

touch container_activity_14.1/container1.txt
```

---

### Step 4: Add Content

```bash
echo "Hello World" > container_activity_14.1/container1.txt
```

Verify:

```bash
cat container_activity_14.1/container1.txt
```

Output:

```text
Hello World
```

---

### Step 5: Create Local Folder

```cmd
mkdir local_activity_14.1
```

Navigate into the folder:

```cmd
cd local_activity_14.1
```

---

### Step 6: Copy Folder from Container

```bash
docker cp ubuntu_container:/home/container_activity_14.1 .
```

---

### Step 7: Validate File Transfer

```cmd
cd container_activity_14.1

type container1.txt
```

Output:

```text
Hello World
```

---

## Folder Structure

### Container

```text
/home
└── container_activity_14.1
    └── container1.txt
```

### Local Machine

```text
local_activity_14.1
└── container_activity_14.1
    └── container1.txt
```

---

## Screenshots Captured

- Step 1: Container Creation
- Step 2: Container CLI
- Step 3: Folder and File Creation
- Step 4: Hello World Content Added
- Step 5a: Local Folder Creation
- Step 5b: Navigation to Local Folder
- Step 6: Successful Docker Copy Command
- Step 7: Validation of Copied File

---

## Key Commands Used

### Create Container

```bash
docker run --name ubuntu_container -dti ubuntu /bin/bash
```

### Copy Folder from Container

```bash
docker cp ubuntu_container:/home/container_activity_14.1 .
```

### Verify Contents

```bash
cat container1.txt
```

or

```cmd
type container1.txt
```

---

## Key Takeaways

- Docker containers have isolated file systems.
- The `docker cp` command allows files and folders to be transferred between a container and a host machine.
- File transfers should always be validated after completion.
- Managing files inside containers is a foundational skill for Docker, DevOps, cloud computing, and data engineering.
- Containerized applications frequently require file movement for datasets, logs, configuration files, backups, and application outputs.

---

## Personal Notes

As a data engineer, I may need to move datasets, configuration files, logs, and processing results between containers and host systems. This activity provided practical experience with Docker file management and reinforced the importance of validating file transfers when working in containerized environments.

---

## Completion Status

```text
✅ Completed
```