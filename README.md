# BuildServer (docker image)

**Docker image used to build projects.**

## This docker image contains
* Ubuntu v21.04
* Latex (full install)
* GNU Make v4.3
* Python v3.9.5
* Go v1.16.5

## Fresh install docker
https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

	curl -fsSL https://get.docker.com -o get-docker.sh; sudo sh get-docker.sh;

### Fetch the latest version of the docker image source

**As an administrator user**

```bash
git clone https://github.com/elarivie/BuildServer.git
cd BuildServer/
wget -O docker_context/go1.16.5.linux-amd64.tar.gz https://golang.org/dl/go1.16.2.linux-amd64.tar.gz
```

### Make sure docker deamon is running

```bash
sudo systemctl status docker
```

### Login using [Docker.com](https://www.docker.com/) credentials
```bash
sudo docker login
```

**⚠**
If you receive the following error when trying to login:

	Error response from daemon: Get https://registry-1.docker.io/v2/: net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)

Then try again and again, try to provide user name and password quickly.

### Build an image

**Note:**
The syntax of the docker build command is

	sudo docker build <dockerfile> <dockercontext>

Where the default value of **dockerfile** is $(pwd)/dockerfile

Where the default value of **dockercontext** is $(pwd)/

You'll notice that within current project the Dockerfile is within the context folder, it does not have to be there but it is just simpler to put everything in the same folder and being able to build using the defaults value with a simple.

```bash
cd docker_context/
sudo docker build .
```

### List images

```bash
sudo docker images
```

### Tag an image
```bash
sudo docker tag a4c2e63a3777 elarivie/buildserver:ubuntu20_10_gnumake_4_3_latex_go_1_16_2
```

### Push an image to [Docker.com](https://www.docker.com/)
```bash
sudo docker push elarivie/buildserver:ubuntu20_10_gnumake_4_3_latex_go_1_16_2
```

### Remove an image
```bash
sudo docker rmi id
```
