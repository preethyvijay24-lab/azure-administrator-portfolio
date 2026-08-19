# Azure Storage Access Troubleshooting Lab

##  Project Overview

This project demonstrates how to troubleshoot and resolve an application data access issue in **Microsoft Azure Blob Storage** using **Microsoft Entra ID** and **Azure Role-Based Access Control (RBAC)**.

The lab simulates a real-world **Application Support incident** where a user is unable to access application data stored in an Azure Blob Storage container.

The issue is investigated using a structured troubleshooting approach, the required RBAC permission is identified and assigned, and access is verified after the resolution.

---
## Table of contents
[Project Objective](#Project Objective)
[Architecture](#Architecture)
[Azure Resources](#Azure Resources)
[ Incident Scenario](# Incident Scenario)
[Screenshots](#Screenshots)

## Project Objective

The main objectives of this project are to:

* Create and configure an Azure Storage Account.
* Create a private Blob Storage container.
* Upload application test data.
* Understand Azure RBAC and data-plane permissions.
* Troubleshoot a simulated user access issue.
* Assign the appropriate Storage Blob Data role.
* Verify that access has been restored.
* Document the incident using an Application Support approach.

---

##  Architecture

```text
                    Microsoft Entra ID
                           │
                           │ Authentication
                           ▼
                    Support User
                           │
                           │ Azure RBAC
                           ▼
                 ┌───────────────────┐
                 │   Azure Storage   │
                 │      Account      │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │  Blob Container   │
                 │ application-data  │
                 └─────────┬─────────┘
                           │
                           ▼
                 application-test.txt
```

---

##  Azure Resources

| Resource        | Name                          |
| --------------- | ----------------------------- |
| Resource Group  | `rg-storage-support-project2` |
| Storage Account | `stappsuport23456`            |
| Blob Container  | `application-data`            |
| Test File       | `application-test.txt`        |
| RBAC Role       | `Storage Blob Data Reader`    |

> Replace `stappsuport23456` with the actual storage account name used in the lab.

# Incident Scenario

### Incident ID

**INC002**

### Incident Title

**User Unable to Access Application Data in Azure Blob Storage**

### Problem Statement

A support user reported that they were unable to access application data stored in an Azure Blob Storage container.

The Storage Account and container were available, but the user did not have the required data-plane permission to access the blob data.

---

## Troubleshooting Process

The issue was investigated using the following approach:

```text
User reports access issue
        ↓
Check Storage Account
        ↓
Check Blob Container
        ↓
Check Microsoft Entra ID user
        ↓
Check Azure RBAC permissions
        ↓
Identify missing data-plane permission
        ↓
Assign Storage Blob Data Reader
        ↓
Allow RBAC propagation
        ↓
Retest blob access
        ↓
Access restored
```

# Implementation Steps

## 1. Create Resource Group

Created the following resource group:

`rg-storage-support-project2`

The resource group provides a logical boundary for the Azure resources used in this project.

---

## 2. Create Storage Account

Created an Azure Storage Account with:

* Standard performance
* Locally Redundant Storage (LRS)
* Microsoft-managed encryption
* Private blob access

The Storage Account is used to store application-related test data.

---

## 3. Create Blob Container

Created a private container:

`application-data`

Anonymous public access was not enabled.

---

## 4. Upload Application Test Data

Uploaded:

`application-test.txt`

The file represents application data that a support user needs to access.

---

## 5. Investigate Access Permissions

Used:

**Storage Account → Access Control (IAM)**

to investigate the user's permissions.

The investigation focused on the difference between:

### Management-plane access

Permissions to manage Azure resources.

### Data-plane access

Permissions to access the actual data stored inside the resource.

A user may be able to manage or view a Storage Account without automatically having permission to read the blob data.

---

## 6. Identify the Required RBAC Role

The required permission for the scenario was:

**Storage Blob Data Reader**

This role provides read access to blob data without granting unnecessary write or delete permissions.

### RBAC Role Comparison

| Role                          | Access                           |
| ----------------------------- | -------------------------------- |
| Storage Blob Data Reader      | Read blob data                   |
| Storage Blob Data Contributor | Read, write and delete blob data |
| Storage Blob Data Owner       | Full control over blob data      |

The **Storage Blob Data Reader** role was selected according to the principle of **least privilege**.

---

## 7. Assign RBAC Permission

Assigned:

**Storage Blob Data Reader**

to the support/test user through:

**Storage Account → Access Control (IAM) → Add Role Assignment**

---

## 8. Verify Access

After the RBAC assignment propagated, the user was able to access the blob:

`application-test.txt`

The access issue was successfully resolved.

# Key Learning

This project helped demonstrate the importance of checking **data-plane permissions** when troubleshooting Azure Storage access issues.

# Screenshots

1. **Azure Resource Group**
   
   <img width="728" height="287" alt="image" src="https://github.com/user-attachments/assets/58b61b07-2bb9-4ae1-a81b-87553abf1257" />

2. **Storage Account Overview**

    <img width="848" height="347" alt="storage account" src="https://github.com/user-attachments/assets/6beb2cb7-400e-4778-bea6-68fb479eedab" />

3. **Blob Container**

   <img width="867" height="268" alt="blob container" src="https://github.com/user-attachments/assets/fca39b20-3163-4dba-a9f5-2f666edcf206" />

4. **Uploaded application test file**

   <img width="842" height="290" alt="test file upload" src="https://github.com/user-attachments/assets/01cfab09-a225-4240-8ab2-ee227f20817c" />

5. **IAM / access investigation**
   
    <img width="873" height="250" alt="access before RBAC" src="https://github.com/user-attachments/assets/9c820092-a303-41ef-a495-01ffa9ad6309" />

6. **Storage Blob Data Reader role assignment**

    <img width="890" height="341" alt="Role assigned" src="https://github.com/user-attachments/assets/46441dc6-1ecd-4814-a389-33ad4cbf1cad" />

7. **Successful blob access**

<img width="706" height="322" alt="test blob access" src="https://github.com/user-attachments/assets/7cda5783-1fbd-47d3-b2bd-696fc4672d0c" />

8. **Disable soft delete**


    <img width="659" height="191" alt="disable soft delete" src="https://github.com/user-attachments/assets/a6c78444-7636-4e37-9df7-41ad72c8d029" />





| Configuration            | After deleting blob                                                     |
| ------------------------ | ----------------------------------------------------------------------- |
| **Soft delete enabled**  | Blob is recoverable during retention period                             |
| **Soft delete disabled** | Blob is permanently deleted and cannot be recovered through soft delete |




**Skills demonstrated:**
Azure Storage | Blob Storage | Microsoft Entra ID | RBAC | Troubleshooting | Incident Management | Application Support

