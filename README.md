# Introduction

This document describes how user can deploy the Keysight CyPerf controller, and agents, along with the Palo Alto VM series firewall and Azure Network Firewall at Azure cloud, inside a Docker Container. The following sections contain information about the prerequisites, deployment, and destruction of setups and config using a sample bash script.

All the necessary resources will be created from scratch, including Vnet, subnets, route table, Security group, Internet Gateway, PAN FW, NGFW etc.

# Prerequisites

- Linux box
- git clone https://github.com/Keysight/pan-demo-tool-azure.git
- Install Docker Engine in your desired host platform if not already. Refer [Install Docker Engine Server](https://docs.docker.com/engine/install/#server) for more details.
- Azure CLI Credentials.
- update terraform.tfvars flies with below parameters
```
azure_stack_name="<short name for your setup>"
azure_location="eastus"
azure_client_id="XXXXXXXXXXXXX"
azure_client_secret="XXXXXXXXXXXXXXX"
azure_tenant_id="XXXXXXXXXXXXXXX"
azure_subscription_id="XXXXXXXXXXXXXXX"
azure_auth_key="<ssh-keygen generated public key content for SSH access>"
azure_allowed_cidr=["<enter your public IP here>"]
azure_license_server="<IP or hostname of CyPerf license server>"
```


# Deploy the setup

A shell script 'pan_demo_setup.sh' will deploy entire topology and configure test for ready to run.

```
pan_demo_setup.sh --deploy
```
# Destroy the setup

```
pan_demo_setup.sh --destroy
```