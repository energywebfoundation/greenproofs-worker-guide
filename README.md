<h1 align="center">
  <br>
  <a href="https://www.energyweb.org/"><img src="https://www.energyweb.org/wp-content/uploads/2019/04/logo-brand.png" alt="EnergyWeb" width="150"></a>
  <br>
  Greenproofs Worker Node
  <br>
  <br>
</h1>


# Deploying Greenproofs Worker Container on a Virtual Machine

This guide covers how to run a containerized worker node on a virtual machine.

## What is a worker node

The worker node is an isolated application that performs some business crucial operations/calculations based only on the received information.

Setting up workers for a dApp: Every Green Proof dApp needs to have multiple worker nodes.

Who can become workers: To become a worker node in a Green Proof system, it needs to have a certain DID-based role (the role can be specified when setting up the system by the platform operator). To have that role, the owner of the account assigned to the worker node needs to be approved by the Governance Body of the Green Proof system. This Governance Body is also defined by the platform operator(s).

## Pre-requisites

- Ensure you have access to create a virtual machine on a cloud provider of choice
- Reach out to devops@energyweb.org for authentication details to the container registry
- Create an `.env` file containing actual values for environment variables gotten from the team

## Minimum Requirement

-   CPU: 2 vCPUs
-   Memory: 4 GB
-   Disk Space: 100 GB
-   Operating System: Ubuntu 20.04 LTS
    

## Step 1: Create a Virtual machine

Create a virtual machine in your cloud provider of choice with the minimum requirements listed in the above section.

## Step 2: Clone Deployment Guide

Clone this [repository](https://github.com/energywebfoundation/greenproofs-worker-guide)

It contains the guide and files required to run the worker image.

## Step 3: Setting up Docker 

Once connected to the VM. Follow the steps below to run the container image.

#### Install docker

`sudo snap install docker`

#### Confirm docker and docker-compose are installed

`docker -v`

`docker-compose -v`

#### Add Docker to sudo group


```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

You can read more about this [here](https://docs.docker.com/engine/install/linux-postinstall/)

### Step 4: Authenticate to Container Registry

In this section, we would login to Docker using a service principal. The service principal application ID ($SP_APP_ID) and the password ($SP_PASSWD) can be gotten from the team.

```bash
SP_APP_ID=$SP_APP_ID
SP_PASSWD=$SP_PASSWD

docker login greenproofsprivatecontainerregistry.azurecr.io --username $SP_APP_ID --password $SP_PASSWD
```

To confirm that this works. You can pull the image from the container registry using the following command:
```
docker pull greenproofsprivatecontainerregistry.azurecr.io/greenproof-worker-app:latest
```

### Step 5: Running the worker node service

Once done, ensure the **.env** file (gotten from the Greenproofs team) is in the same directory as the **docker-compose.yml** file and contains all environment variables required. 

Finally, run the command

`docker-compose up -d`

This would bring up the worker node service. 

You can reach out to the team for further help or check out the Docker Compose cheat sheet for more debugging tips [here](https://dockerlabs.collabnix.com/intermediate/docker-compose/compose-cheatsheet.html "https://dockerlabs.collabnix.com/intermediate/docker-compose/compose-cheatsheet.html")
