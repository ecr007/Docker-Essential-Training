# Docker Expained

Docker uses images and containers to allow apps to run anywhere consistently.

## Previous Solutions

- Configuration Maganament Tools (Chef, Puppet and Ansible) these required knowledge aboud hardware and operating systems.

- Virtual machine as code (Vagrant) heavy, slow-ish, requires inconvenient configuration.

## Docker makes containers easy

1 - Configuration through Dockerfiles, not shell command.

2 - Share images with others through images registries. 

3 - A super easy command line client and API.

## What are Docker Containers not doing?

* Containers are not smaller Virtual Machines (VMs)

<img src="imgs/docker-vs-vms.png" />

**Containers vs Virtual Machines**

**Containers**

- Run in containers runtimes.
- Work alongside operating systems.
- Do not required OS configuration.
- Run one app at a time. (usually)

**Virtual Machines**

- Run on top of hypervisors. 
- Need hardware emulations.
- Require OS configuration.
- Can run many apps at once. 

## Container runtimes

**How do containers even work?**

Container runtimes create, manage and delete containers.

**Container runtimes automate all these with one command ```docker run```**

In the host:
- Mount a directory
- Unshare a namespace 
- Create a chroot pointed to de mounted directory.

In the namespace
- Create a control group and bind to PID within namespace.
- Set Linux capabilities on the chroot.
- Start application within the namespace. 

Container runtimes can:
- Create namespaces.
- Create and associate cgroups to namespaces (containers)
- Map filesystems to containers.
- Set container capabilities.
- Start, stop, and remove individual containers.

Cannot: 
- Build images.
- Pull images.
- Serve API for interacting with containers.

## OCI and CRI runtimes

Types of containers runtimes

**OCI** The Open Cointainer Initiative is a working group.

- OCI aims to standatize container technology like container images and runtimes.
- The OCI runtimes specification outlines what a container is and how they should be manage.
- runtime-spec does not dicate how to do these things 
- **runc** from docker is de facto industry standard runtime.


