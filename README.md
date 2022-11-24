# Deploying Greenproofs Worker Container on Virtual Machine


This covers creating a virtual machine Azure cloud environment to run the Greenproofs worker node.

The worker node is containerized and can be run on a virtual machine.

## Requirement

-   CPU: 2 vCPUs
-   Memory: 4 GB
-   Disk Space: 100 GB
-   Operating System: Ubuntu 20.04 LTS
    

## Create a Virtual machine

To create a virtual machine in your cloud provider. Ensure the virtual machine matches the minimum requirements listed in the above section.

## Deployment Guide

Clone this repository

It contains the guide and files required to run the worker image.

## Deploying Worker Image to Virtual Machine

Once connected to the VM. Follow the steps to run the container image.

#### Install docker

`sudo snap install docker`

#### Confirm docker and docker-compose are installed

`docker -v`

`docker-compose -v`

#### Application setup

Once done, ensure to the **.env** file contains all environment variables required in the same directory as the **docker-compose.yml** file.

Finally, run the command

`docker-compose up -d`

This would bring up all services. You can reach out to the team for further help or check out the Docker Compose cheat sheet for more debugging tips [here](https://dockerlabs.collabnix.com/intermediate/docker-compose/compose-cheatsheet.html "https://dockerlabs.collabnix.com/intermediate/docker-compose/compose-cheatsheet.html")
