# Docker
[Docker](https://www.docker.com/) is a tool which is used to automate the deployment of applications in lightweight containers that applications can work efficiently in different environments.

*Note: Container is a software package that consists of all the dependencies required to run an application*

## Docker vs Virtual Machine
| Criteria   | Virtual Machine |  Docker |
|----------|:-------------:|:------:|
| OS support |  Occupies a lot of memory space | Docker Containers occupy less space |
| Boot-up time | Long boot-up time | Short boot-up time |
| Performance | Running multiple virtual machines leads to unstable performance | Containers have a better performance as they are hosted in a single Docker engine |
| Scaling | Difficult to scale up | Easy to scale up |
| Efficiency | Low efficiency | High efficiency |
| Portability | Compatibility issues while porting across different platforms | Easily portable across different platforms |
| Space allocation | Data volumes cannot be shared | Data volumes can be shared and reused among multiple containers |

## How does Docker work?
### Docker engine overview
```
[Client (Docker CLI)] <--- [REST API] ---> [Server (Docker Daemon)]
```
* Docker Engine or Docker is the base engine installed on your host machine to build and run containers using Docker components and services
* It  uses client-server architecture
* Docker Client and Server communicate REST API
* Docker Client is a service which runs a command. The command is translated using REST API and is sent to the Docker Daemon (server)
* Then, Docker Daemon checks the client request and interacts with the operating system in order to create or manage containers


### Components of Docker
#### Docker Client and Server
* Docker Client is accessed from the terminal and a Docekr Host runs the Docker Daemon and registry
* A user can build Docker Images and run Docker Containers by passing commands from the Docker Client to Docker Server

#### Docker Images
* Docker Image is a template with instructions, which is used for creating Docker Containers
* A Docker Image is built using a file called Docker File (*A Docker file is a text file which contains commands for building a Docker Image*)
* Docker Image is stored in a Docker Hub or in a repository

#### Docker Containers
* Docker Container is a standalone, executable software package which includes applications and their dependencies* 
* Numerous Docker Containers run on the same infrastructure and share operating system with its other containers
* Each container runs in isolation

#### Docker Registry
* Docker Registry is an open source server-side service used for hosting and distributing images
* Docker also has its own default registry called Docker Hub (public)
* Images can be stored either public or private repositories
* Pull (download) and Push (upload) are the commands used by users in order to interact with a Docker Registry

## Sources
[What Is Docker? | What Is Docker And How It Works? | Docker Tutorial For Beginners | Simplilearn - Simplilearn](https://www.youtube.com/watch?v=rOTqprHv1YE)
