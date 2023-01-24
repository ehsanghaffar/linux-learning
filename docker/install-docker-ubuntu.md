# Install Docker Engine on Ubuntu
>
> from official docs

To get started with Docker Engine on Ubuntu, make sure you meet the prerequisites, then install Docker.

## OS requirements

> To install Docker Engine, you need the 64-bit version of one of these Ubuntu versions:

- Ubuntu Kinetic 22.10
- Ubuntu Jammy 22.04 (LTS)
- Ubuntu Focal 20.04 (LTS)
- Ubuntu Bionic 18.04 (LTS)

### Install using the repository

> Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

#### Set up the repository

1 . Update the ``apt`` package index and install packages to allow ``apt`` to use a repository over HTTPS:

  ```bash
  sudo apt-get update
  sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
  ```

2 . Add Docker’s official GPG key:

```bash
 sudo mkdir -p /etc/apt/keyrings
 curl -fsSL <https://download.docker.com/linux/ubuntu/gpg> | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3 . Use the following command to set up the repository:

```bash
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] <https://download.docker.com/linux/ubuntu> \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### Install Docker Engine

1 . Update the apt package index:

```bash
 sudo apt-get update
```

2 . Receiving a GPG error when running apt-get update?

Your default umask may be incorrectly configured, preventing detection of the repository public key file. Try granting read permission for the Docker public key file before updating the package index:

```bash

 sudo chmod a+r /etc/apt/keyrings/docker.gpg
 sudo apt-get update
```

3 . Install Docker Engine, containerd, and Docker Compose.

- To install the latest version, run:

    ```bash
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
    ```

- Verify that the Docker Engine installation is successful by running the hello-world image:

    ```bash
    sudo docker run hello-world
    ```

This command downloads a test image and runs it in a container. When the container runs, it prints a
confirmation message and exits.
