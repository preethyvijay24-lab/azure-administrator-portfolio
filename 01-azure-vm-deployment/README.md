# Azure VM Deployment and Secure Networking

## Project Overview

This project demonstrates the deployment and management of a Windows virtual machine in Microsoft Azure, with a focus on networking, security, access control, monitoring, and resource management.

The project was completed as part of my hands-on preparation for the Microsoft Azure Administrator (AZ-104) certification.

## Objectives

* Deploy an Azure Virtual Machine
* Create and configure an Azure Virtual Network
* Configure a subnet for the virtual machine
* Configure a Network Security Group (NSG)
* Secure RDP access
* Verify VM networking and connectivity
* Review Azure RBAC permissions
* Monitor VM performance
* Document the implementation
* Clean up Azure resources after testing

## Azure Services Used 

* Azure Virtual Machines
* Azure Virtual Network
* Subnet
* Network Security Group
* Public IP Address
* Network Interface
* Azure Role-Based Access Control (RBAC)
* Azure Monitor / Metrics
* Resource Groups

## Architecture

```text
                    Internet
                       |
                       | RDP
                       v
                 Public IP
                       |
                       v
                Network Security
                    Group
                       |
                       v
                  Azure VNet
                       |
                  subnet-vm
                       |
                       v
                Windows VM
```

## Implementation

### 1. Resource Group

Created the resource group:

`rg-az104-vm-project`

The resource group was used to organize all resources associated with this lab.

### 2. Virtual Machine

Deployed a Windows Server virtual machine:

`vm-az104-demo`

The VM was configured with a virtual network, subnet, network interface, public IP address and Network Security Group.

### 3. Virtual Network

Created:

`vnet-az104-demo`

Configured a dedicated subnet:

`subnet-vm`

### 4. Network Security Group

Created:

`nsg-vm-az104`

Configured inbound access for RDP while restricting the source to the required IP address rather than exposing RDP broadly to the internet.

### 5. Remote Connectivity

Verified successful RDP connectivity to the Windows virtual machine.

### 6. Azure RBAC

Reviewed role assignments through Azure Access Control (IAM).

The project demonstrates the relationship between:

* Principal
* Role
* Scope

### 7. Monitoring

Reviewed VM metrics such as CPU and network activity using Azure monitoring capabilities.

## Screenshots

### VM Overview
<img width="937" height="361" alt="01-vm-overview" src="https://github.com/user-attachments/assets/d3420f0d-8ee7-4f48-b2c6-19ce634cd756" />

### VM Networking
<img width="931" height="370" alt="02-vm-networking" src="https://github.com/user-attachments/assets/bbf8d338-5820-4423-96f1-a3e9b26eb35c" />

### NSG Inbound Rules
<img width="941" height="374" alt="03-nsg-inbound-rules" src="https://github.com/user-attachments/assets/6f5afb75-06a0-4fef-970f-3ce2e7effaeb" />

### VM Monitoring
<img width="941" height="373" alt="04-vm-monitoring" src="https://github.com/user-attachments/assets/6cd81ca1-e153-4b41-a124-8398c1fefdfd" />

### RBAC
<img width="932" height="355" alt="06-IAM role" src="https://github.com/user-attachments/assets/b154bb90-efcb-4bf5-a15b-9688aa6f8049" />
<img width="452" height="412" alt="windows server desktop" src="https://github.com/user-attachments/assets/4bd380bd-4ff9-4228-870e-3ff06888de87" />

## Key AZ-104 Concepts Practiced

* Resource Groups
* Virtual Machines
* Managed Disks
* Virtual Networks
* Subnets
* Network Security Groups
* Public and Private IP addresses
* RDP connectivity
* Azure RBAC
* Access Control (IAM)
* Azure Monitoring
* Resource cleanup        

## Key Learnings

Through this project, I gained hands-on experience deploying and managing Azure virtual machines and learned how networking, security rules, access control and monitoring work together.

I also practiced securing remote access by restricting network access instead of allowing unrestricted inbound RDP traffic.

## Cleanup

After completing the lab, the resource group and associated resources were removed to avoid unnecessary Azure consumption.

## Skills Demonstrated

`Microsoft Azure` `Azure VM` `VNet` `Subnet` `NSG` `RBAC` `Azure Monitor` `Cloud Administration` `Troubleshooting`
