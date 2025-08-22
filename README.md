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

NB: [List is empty, because i don't have any container running at this momemnt]
```
#### 01: Check list of all container including stop containers
```bash
docker ps -a

Output: 

CONTAINER ID   IMAGE               COMMAND                  CREATED          STATUS                     PORTS                    NAMES
b157be5e6344   hello-world         "/hello"                 54 minutes ago   Exited (0) 5 minutes ago                            vibrant_turing
fb9501a951ad   bitnami/kafka:3.7   "/opt/bitnami/script…"   3 days ago       Exited (143) 2 days ago                             kafka
a80935efa3cb   redis               "docker-entrypoint.s…"   6 weeks ago      Exited (255) 4 days ago    0.0.0.0:6379->6379/tcp   redis-server
```



