# **Linux File System Navigation Lab**

## **Project Introduction**

This repository contains a detailed walkthrough of a hands-on lab activity focused on fundamental Linux command-line operations for file system navigation and file content manipulation. As a security analyst, the ability to efficiently navigate, locate, and read files remotely via a Linux shell (without a graphical user interface) is a critical skill for tasks such as investigating unauthorized access, analyzing logs, and managing system configurations.

## **Scenario**

The lab scenario involved navigating a specific Linux file structure within the /home/analyst directory to locate and analyze information from various files. This included:

* Identifying the current working directory and its contents.  
* Changing directories and listing subdirectories.  
* Locating and reading the full contents of a specific file (Q1\_added\_users.txt).  
* Navigating to another directory (logs) and displaying the first 10 lines of a log file (server\_logs.txt).

## **Tools and Commands Used**

* **Operating System:** Debian-based Linux (within a virtual machine)  
* **Shell:** Bash  
* **Commands:**  
  * pwd: Print Working Directory  
  * ls: List directory contents  
  * cd: Change Directory  
  * cat: Concatenate files and print on the standard output (used to display file contents)  
  * head: Output the first part of files (used to display the beginning of a file)

## **Lab Walkthrough and Results**

The full, step-by-step execution of the lab, including all commands and their corresponding outputs, is documented in the Linux\_File\_System\_Navigation\_Lab\_Report.md file within this repository. This report serves as a complete record of the practical activity.

## **Key Learnings**

This activity provided valuable hands-on experience in:

* **Linux File System Structure:** Understanding hierarchical directory organization.  
* **Basic Navigation:** Efficiently moving between directories using absolute and relative paths.  
* **File Listing:** Identifying files and subdirectories within a given path.  
* **File Content Viewing:** Using cat for full file content and head for partial content, which is crucial for large log files.  
* **Problem Solving:** Applying learned commands to answer specific questions based on file content.