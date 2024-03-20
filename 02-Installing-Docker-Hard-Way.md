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

