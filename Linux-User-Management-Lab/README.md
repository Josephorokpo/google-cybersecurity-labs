# **Linux User Management Lab**

## **Project Introduction**

This repository contains a detailed walkthrough of a hands-on lab activity focused on managing user access in a Linux Bash shell. As a security analyst, understanding and implementing proper user authentication and authorization is fundamental to maintaining system security. This lab explores key commands for adding, modifying, and deleting users and their associated permissions and group memberships.

## **Scenario**

The lab scenario simulates a common organizational task: managing a new employee's access throughout their tenure. This includes adding a new user (researcher9), assigning them file ownership, adding them to secondary groups, and eventually deleting their account from the system. All operations require elevated privileges, emphasizing the use of sudo.

## **Tools and Commands Used**

* **Operating System:** Debian-based Linux (within a virtual machine)  
* **Shell:** Bash  
* **Privilege Escalation:** sudo  
* **Commands:**  
  * useradd: Create a new user account.  
  * usermod: Modify user account properties (e.g., primary/secondary groups).  
  * chown: Change file owner and group.  
  * userdel: Delete a user account.  
  * groupdel: Delete a group.

## **Lab Walkthrough and Results**

The full, step-by-step execution of the lab, including all commands executed and their corresponding outputs, is documented in the Linux\_User\_Management\_Lab\_Report.md file within this repository. This report serves as a complete record of the practical activity.

## **Key Learnings**

This activity provided valuable hands-on experience in:

* **User Account Creation:** Adding new users to a Linux system.  
* **Primary Group Management:** Assigning a user's primary group.  
* **File Ownership Transfer:** Changing the owner of files.  
* **Secondary Group Management:** Adding users to supplementary groups.  
* **User Account Deletion:** Removing users and their associated groups from the system.  
* **Privilege Management (sudo):** Understanding the necessity of elevated privileges for user and group administration.