# Video 14.7: Uploading and Downloading Files to and from Containers

## Duration

**4:35**

---

# Overview

In this video, Dr. Sanchez demonstrates how to transfer files between a local computer and a Docker container.

File transfers are an essential skill when working with containers because containers often run in isolated environments. Developers frequently need to move source code, configuration files, datasets, and output files between the host machine and running containers.

---

# Learning Objectives

After completing this video, you should be able to:

- Copy files from a local machine to a Docker container.
- Copy files from a Docker container to a local machine.
- Understand the purpose of the `docker cp` command.
- Manage files inside containerized environments.

---

# Why File Transfers Are Important

Containers are isolated from the host operating system.

As a result, files that exist on your local machine are not automatically available 