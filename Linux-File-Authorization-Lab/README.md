# **Linux File Authorization Lab**

## **Project Introduction**

This repository contains a detailed walkthrough of a hands-on lab activity focused on configuring authorization in Linux systems. Authorization, which involves granting specific access rights to resources, is a critical security measure. Without proper authorization, any user could potentially access and modify sensitive files, posing a significant security risk.

In this lab, we explore Linux file and directory permissions, and practice changing file/directory ownership and permissions to enforce access control. As a security analyst, understanding and setting appropriate access permissions is vital for protecting sensitive information and maintaining overall system security.

## **Scenario**

The lab scenario involved examining and managing permissions on files and directories within the /home/researcher2/projects directory, where the researcher2 user is part of the research\_team group. The goal was to ensure that all file and directory permissions aligned with the required authorization, and to correct any discrepancies.

## **Tools and Commands Used**

* **Operating System:** Debian-based Linux (within a virtual machine)  
* **Shell:** Bash  
* **Commands:**  
  * cd: Change Directory  
  * ls \-l: List directory contents in long format (showing permissions, ownership, etc.)  
  * ls \-la: List directory contents in long format, including hidden files.  
  * chmod: Change file modes or access control lists (permissions).

## **Lab Walkthrough and Results**

The full, step-by-step execution of the lab, including all commands executed and their corresponding outputs, is documented in the Linux\_File\_Authorization\_Lab\_Report.md file within this repository. This report serves as a complete record of the practical activity.

## **Key Learnings**

This activity provided valuable hands-on experience in:

* **Understanding Linux Permissions:** Interpreting the 10-character permission string (rwx for user, group, and others).  
* **Identifying Hidden Files:** Using ls \-la to reveal hidden files and their permissions.  
* **Changing File Permissions (chmod):**  
  * Removing specific permissions for "other" (o-w).  
  * Removing specific permissions for a "group" (g-r).  
  * Modifying multiple permissions simultaneously (u-w,g-w,g+r).  
* **Changing Directory Permissions:** Restricting access to directories.  
* **Security Best Practices:** The importance of least privilege in file and directory access.