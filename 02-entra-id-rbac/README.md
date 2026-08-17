# Microsoft Entra ID and Azure RBAC — Secure Access Management

## Project Overview

This project demonstrates identity and access management in Microsoft Azure using Microsoft Entra ID and Azure Role-Based Access Control (RBAC).

The project was completed as part of my hands-on preparation for the Microsoft Azure Administrator (AZ-104) certification.

The objective was to create test identities, organize users into a security group, assign an Azure RBAC role, and verify the role assignment at resource-group scope.

## Objectives

* Create Microsoft Entra ID users
* Create a security group
* Add users to the security group
* Assign an Azure RBAC role
* Understand RBAC scope
* Apply the principle of least privilege
* Verify role assignments
* Document the implementation

## Azure Services Used

* Microsoft Entra ID
* Azure RBAC
* Azure Resource Groups
* Microsoft Azure Portal

## Architecture

<img width="536" height="455" alt="architecture" src="https://github.com/user-attachments/assets/5cf01bda-1a5c-4240-ad3c-ca3a12e89e9c" />


## Implementation

### 1. Resource Group

Created the resource group:

`rg-az104-vm-project`

This resource group was used as the scope for the Azure RBAC assignment.

### 2. Microsoft Entra ID Users

Created test identities for the lab:

* Azure Admin Lab
* VM Operator Lab

These identities were created for demonstrating identity and access management concepts.

### 3. Security Group

Created the Microsoft Entra security group:

`AZ104-VM-Admins`

The VM Operator Lab user was added to the group.
`AZ104 Test User`

### 4. Azure RBAC Assignment

Assigned the following role:

`Contributor`

The role was assigned to:

`AZ104-VM-Admins`

At the following scope:

`rg-az104-vm-project

The RBAC assignment demonstrates the relationship between:

* Principal
* Role
* Scope

### 5. Least Privilege

Instead of assigning broad Owner or Contributor permissions, a more specific role was selected based on the intended VM management requirement.

This demonstrates the principle of least privilege.

## Screenshots

### Entra ID Group Members
<img width="890" height="319" alt="01-entra-group-members" src="https://github.com/user-attachments/assets/54d1b9a1-e881-4e8b-851f-ff859f67cbdf" />

### RBAC Role Assignment
<img width="803" height="323" alt="02-rbac-role-assignment" src="https://github.com/user-attachments/assets/24f8c2bf-a8d0-40df-b6d8-c6844031de51" />

### RBAC Scope
<img width="930" height="334" alt="03-rbac-test vm1" src="https://github.com/user-attachments/assets/04851097-98f6-4356-bef2-b0f07998f8d2" />

### RBAC denied after role assignment removed
<img width="930" height="334" alt="03-rbac-test vm" src="https://github.com/user-attachments/assets/c851ec0a-a680-4625-b247-f87a59396fbe" />

## Key AZ-104 Concepts Practiced

* Microsoft Entra ID
* Users
* Security Groups
* Azure RBAC
* Built-in Roles
* Role Assignments
* Principal
* Role
* Scope
* Resource Group Scope
* Least Privilege
* Identity and Access Management

## Key Learning

Microsoft Entra ID is used to manage identities such as users and groups, while Azure RBAC controls what those identities can access and what actions they can perform on Azure resources.

## Skills Demonstrated

`Microsoft Azure` `Microsoft Entra ID` `Azure RBAC` `IAM` `Security Groups` `Role Assignments` `Least Privilege` `Cloud Administration`

