# Deploying Greenproofs Worker Container on a Virtual Machine

The containerized worker node and can be run on a virtual machine with Docker installed

## Minimun Requirement

-   CPU: 2 vCPUs
-   Memory: 4 GB
-   Disk Space: 100 GB
-   Operating System: Ubuntu 20.04 LTS
    

## Create a Virtual machine

Create a virtual machine in your cloud provider of choice with the minimum requirements listed in the above section.

## Deployment Guide

Clone this [repository](https://github.com/energywebfoundation/greenproofs-worker-guide)


It contains the guide and files required to run the worker image.

## Deploying Worker Image 

Once connected to the VM. Follow the steps to run the container image.

#### Install docker

`sudo snap install docker`

#### Confirm docker and docker-compose are installed

`docker -v`

`docker-compose -v`

### Add Docker to Sudo Group


```
sudo groupadd docker
sudo usermod -aG docker $user
```

#### Application setup

Once done, ensure to the **.env** file contains all environment variables required in the same directory as the **docker-compose.yml** file.

Finally, run the command

`docker-compose up -d`

This would bring up all services. You can reach out to the team for further help or check out the Docker Compose cheat sheet for more debugging tips [here](https://dockerlabs.collabnix.com/intermediate/docker-compose/compose-cheatsheet.html "https://dockerlabs.collabnix.com/intermediate/docker-compose/compose-cheatsheet.html")
