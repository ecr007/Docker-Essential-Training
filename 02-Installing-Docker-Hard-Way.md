# Installing Docker: The Hard Way

Its the best method to install Docker, because:

- Cost effective solution for large teams.
- You want to run Docker Remotely.
- You need more control over the virtual machine that is created for you.

## Installing Lima

Lima is a lightweight virtual machine manager that deploy virtual machines through the "QEMU Hypervisor" than Virtual Machine or VMWare Fusin.

```brew install lima```

## Configuring Lima

Lima uses YAML based configuration file to define and start virtual machine. 

Firstly, downloand Docker-Rootful.yaml file:
https://github.com/lima-vm/lima/blob/master/examples/docker-rootful.yaml

- Images: pre-packaged virtual machines or images. Lima try line by line if one of them not found. 

- Mounts: list of directories, you can set capability. 

- Provision: define series and scripts to run against a virtual machine after it boots 

    - mode : code related Docker installation. 

## Starting the Lima VM

Lima comes with two command line tools. 

```limactl``` (lima command line client), use for stop or start lima VM. 

**Available Command**

- limactl --help : to see all command. 

- limactl start or limactl start

- limactl --name : to provide a name of virtual machine.

- limactl --tty : this tell lima whether it should open an editor. So that we can after that file that we dowloanded earlier in case we run into problems. 


**Starting**
use to create Virtual Machine.

```
limactl start docker-rootful.yaml --name "Container NAME" --tty=false 
```

After installing, we can see options for connections your docker local to the docker engine in the VM. Copy it and save for later. 

```
# Use it to test docker after install it.

To run `docker` on the host (assumes docker-cli is installed), run the following commands:
------

# 1) This first instructions creates an object called the context. It maps a path to a docker engine unix socket.
docker context create lima-myDocker --docker "host=unix:///Users/OS NAME/.lima/myDocker/sock/docker.sock"

# 2) Tells docker to use this context that we just created as default. If you didn't do this, docker would think that the docker engine is running with the first option command. 
docker context use lima-myDocker

# 3) Finally, the last command creates and starts a new container from an image in the docker hub called hello-world  
docker run hello-world
------

```

**Install Docker From terminal**

```
brew install docker
```

it install docker-cli not the docker desktop program. 

**Docker Hub** Is a public repository of container images that anyone can use or publish to. 

## Docker Host

**Another way to specific the docker.sock**

Advantages:

- It doesn't save any extra data like creating a context does.
- Docker context is a new features of Docker CLI .

```
export DOCKER_HOST="unix:///Users/OS NAME/.lima/myDocker/sock/docker.sock"

# test
docker context remove lima-myDocker
docker run whatever-you-want
```
