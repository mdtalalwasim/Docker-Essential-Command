# Docker-Essential-Command
Docker-Essential-Command

I am going to share some important Docker commands [on linux machine] which will help you to work with docker and also learn docker basic for docker beginners.

#### 01: Check docker version
```bash
docker --version

Output: 
Docker version 28.3.1, build 38b7060
```
#### 02: Check docker version
```bash
docker version

Output: 
Client: Docker Engine - Community
 Version:           28.3.1
 API version:       1.48 (downgraded from 1.51)
 Go version:        go1.24.4
 Git commit:        38b7060
 Built:             Wed Jul  2 20:56:27 2025
 OS/Arch:           linux/amd64
 Context:           desktop-linux

```

#### 03: Check list of running containers
```bash
docker ps


Output: 
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES


```
**NB: [List is empty, because i don't have any container running at this momemnt]**

#### 04: Check list of all container including stop containers
```bash
docker ps -a

Output: 

CONTAINER ID   IMAGE               COMMAND                  CREATED          STATUS                     PORTS                    NAMES
b157be5e6344   hello-world         "/hello"                 54 minutes ago   Exited (0) 5 minutes ago                            vibrant_turing
fb9501a951ad   bitnami/kafka:3.7   "/opt/bitnami/script…"   3 days ago       Exited (143) 2 days ago                             kafka
a80935efa3cb   redis               "docker-entrypoint.s…"   6 weeks ago      Exited (255) 4 days ago    0.0.0.0:6379->6379/tcp   redis-server
```
#### 05: List of All Images
```bash
docker images


Output: 

REPOSITORY      TAG       IMAGE ID       CREATED        SIZE
hello-world     latest    1b44b5a3e06a   13 days ago    10.1kB
redis           latest    f2cd22713a18   6 weeks ago    128MB
bitnami/kafka   3.7       cb4410499b04   8 months ago   648MB```

```

#### 06: Delete Container
```bash
docker rm <container_id>

docker rm b157be5e6344

Output:
b157be5e6344


NB: Your container will remove after executing the above command.


```
Here, **rm** means - remove
#### 06: Delete Image
```bash
docker rmi <image_id>

docker rmi 1b44b5a3e06a

Output: 
Untagged: hello-world:latest
Untagged: hello-world@sha256:a0dfb02aac212703bfcb339d77d47ec32c8706ff250850ecc0e19c8737b18567
Deleted: sha256:1b44b5a3e06a9aae883e7bf25e45c100be0bb81a0e01b32de604f3ac44711634
Deleted: sha256:53d204b3dc5ddbc129df4ce71996b8168711e211274c785de5e0d4eb68ec3851


```
#### NB: Your image will remove after executing the above command.
Here, **rmi** means -- remove image
####  Special Note: 
- Before removing any image, you must remove its container first.
- Each time a **a new container id** will assign while running a new container.




### Workflow
**1. First, Search for an image in Docker Hub**
 
```bash
docker search <image_name>

docker search hello-world

Output: 

NAME                                DESCRIPTION                                     STARS     OFFICIAL
hello-world                         Hello World! (an example of minimal Dockeriz…   2480      [OK]
rancher/hello-world                 This container image is no longer maintained…   6         
okteto/hello-world                                                                  0         
goharbor/hello-world                                                                0         
atlassian/hello-world                                                               1         
tutum/hello-world                   Image to test docker deployments. Has Apache…   91        
dockercloud/hello-world             Hello World!                                    20        
crccheck/hello-world                Hello World web server in under 2.5 MB          26        
koudaiii/hello-world                                                                0         
ppc64le/hello-world                 Hello World! (an example of minimal Dockeriz…   2         
tsepotesting123/hello-world                                                         0         
prajwalendra/hello-world                                                            0         
kevindockercompany/hello-world                                                      0         
infrastructureascode/hello-world    A tiny "Hello World" web server with a healt…   1         
arm32v7/hello-world                 Hello World! (an example of minimal Dockeriz…   3         
cloudflare/hello-world              A simple example application which can be ru…   0         
datawire/hello-world                Hello World! Simple Hello World implementati…   1         
uniplaces/hello-world                                                               0         
twistlocktest/hello-world                                                           0         
wjimenez5271/hello-world                                                            0         
arm64v8/hello-world                 Hello World! (an example of minimal Dockeriz…   3         
danfengliu/hello-world                                                              0         
lbadger/hello-world                                                                 0         
ansibleplaybookbundle/hello-world   Simple containerized application that tests …   0         
kousik93/hello-world
```
**NB: Official [OK] means Official Image from Docker.**

**2. Second, pull *hello-world* image from docker hub.**
```bash
docker pull <image_name> [replace with your desire image_name]

docker pull hello-world

Output:


Using default tag: latest
latest: Pulling from library/hello-world
17eec7bbc9d7: Pull complete 
Digest: sha256:a0dfb02aac212703bfcb339d77d47ec32c8706ff250850ecc0e19c8737b18567
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest


```
**Check Docker Images List (Before pulling new image *hello-world* from docker hub):**
```bash
docker images

Output:
REPOSITORY      TAG       IMAGE ID       CREATED        SIZE
redis           latest    f2cd22713a18   6 weeks ago    128MB
bitnami/kafka   3.7       cb4410499b04   8 months ago   648MB

```


**Check Docker Images List (After pulling new image *hello-world* from docker hub):** 
```bash
docker images

Output:
REPOSITORY      TAG       IMAGE ID       CREATED        SIZE
hello-world     latest    1b44b5a3e06a   13 days ago    10.1kB
redis           latest    f2cd22713a18   6 weeks ago    128MB
bitnami/kafka   3.7       cb4410499b04   8 months ago   648MB

```
**NB:** See hello-world is added into the image list

**3. Check Container List**

```bash
docker ps -a

Output:
CONTAINER ID   IMAGE               COMMAND                  CREATED       STATUS                    PORTS                    NAMES
fb9501a951ad   bitnami/kafka:3.7   "/opt/bitnami/script…"   3 days ago    Exited (143) 2 days ago                            kafka
a80935efa3cb   redis               "docker-entrypoint.s…"   6 weeks ago   Exited (255) 4 days ago   0.0.0.0:6379->6379/tcp   redis-server

```
**N.B:** See there is no *hello-world* image container is created, because we need to create it first.

**4. Create a container from image**

```bash
docker create <image_name>

docker create hello-world

Output:
c3628e97d00465ea3b5cbf43bc1ec6a626e68b912a1f0629937d0c315a1e775c


```
**Check Docker Container List (After creating new container from image):** 
```bash

docker ps -a

CONTAINER ID   IMAGE               COMMAND                  CREATED          STATUS                    PORTS                    NAMES
c3628e97d004   hello-world         "/hello"                 12 seconds ago   Created                                            quirky_payne
fb9501a951ad   bitnami/kafka:3.7   "/opt/bitnami/script…"   3 days ago       Exited (143) 2 days ago                            kafka
a80935efa3cb   redis               "docker-entrypoint.s…"   6 weeks ago      Exited (255) 4 days ago   0.0.0.0:6379->6379/tcp   redis-server

```
**N.B** See there is new container added into the list with *Container ID : c3628e97d004*
