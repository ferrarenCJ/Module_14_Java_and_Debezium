# Coding Activity 14.1: Uploading and Downloading Files to and from Containers

## Objective

Practice moving files and directories between a Docker container and a local machine using the `docker cp` command.

## Commands Used

### Create Container

```bash
docker run --name ubuntu_container -dti ubuntu /bin/bash