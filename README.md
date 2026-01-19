# Active Directory Lab: Implementing Tiered Organizational Units (OUs)

**WATCH THE VIDEO HERE**

https://www.loom.com/share/db8db05333cb4dae999164bbae40a077

# Project Overview

This lab demonstrates the configuration of a Windows-based identity management system using AWS EC2 and Active Directory Domain Services (AD DS). The project focused on building a scalable, nested Organizational Unit (OU) structure to facilitate efficient object management and Group Policy (GPO) application.

# Technologies Used
Cloud Provider: AWS (EC2)

Operating System: Windows Server 2022

Role: Active Directory Domain Services (AD DS)

Tools: Active Directory Users and Computers (ADUC)

# Implementation Steps
**1. Environment Provisioning**
Deployed a Windows Server instance on AWS EC2.

Configured Security Groups to allow administrative RDP access and internal domain traffic.

Installed the AD DS Role and promoted the server to a Domain Controller for a new forest.

**2. Building the "Global" Root OU**
To separate production objects from default system containers, I established a top-level hierarchy:

Opened Active Directory Users and Computers (ADUC).

Created a new OU titled "Global".

Security Note: Ensured the "Protect container from accidental deletion" checkbox was enabled to prevent administrative errors.

**3. Implementing the Nested Tiered Structure**
Under the "Global" parent OU, I created two functional sub-units to categorize objects by type. For each of these, I maintained the "Protect from accidental deletion" setting for increased environment stability.

LAB_Standard_users: Dedicated container for all non-administrative user accounts.

LAB_Workstations: Dedicated container for computer objects and virtual desktops joined to the domain.

# Key Results & Security Hardening
**Accidental Deletion Protection:** By checking the "Protect from accidental deletion" box, the Object tab in the OU properties now requires an explicit permission change before the OU can be removed, preventing catastrophic accidental loss of directory structure.

**Inheritance Readiness:** This structure is now prepared for Group Policy Objects (GPOs). I can now apply security baseline policies to LAB_Workstations without affecting the LAB_Standard_users.

