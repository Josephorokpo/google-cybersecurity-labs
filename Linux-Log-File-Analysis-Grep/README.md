# **Linux Log File Analysis with Grep**

## **Project Introduction**

This repository contains a detailed walkthrough of a hands-on lab activity focused on advanced command-line filtering in Linux using the powerful grep command and piping (|). As a security analyst, the ability to efficiently search for specific information within large log files and identify files based on naming conventions is paramount for incident investigation, threat hunting, and system auditing.

## **Scenario**

The lab scenario involved obtaining specific information from server logs and user data files, as well as finding files with particular strings in their names, all within the /home/analyst directory structure.

## **Tools and Commands Used**

* **Operating System:** Debian-based Linux (within a virtual machine)  
* **Shell:** Bash  
* **Commands:**  
  * cd: Change Directory  
  * grep: Global Regular Expression Print (used for searching text patterns)  
  * ls: List directory contents  
  * |: Pipe (used to direct the output of one command as input to another)

## **Lab Walkthrough and Results**

The full, step-by-step execution of the lab, including all commands executed and their corresponding outputs, is documented in the Grep\_Filtering\_Lab\_Report.md file within this repository. This report serves as a complete record of the practical activity.

## **Key Learnings**

This activity provided valuable hands-on experience in:

* **Efficient Log Analysis:** Quickly extracting relevant information (e.g., error messages) from large text files.  
* **Command Chaining (Piping):** Combining ls and grep to filter file listings.  
* **Targeted Search:** Using grep to find specific strings within file contents.  
* **Regular Expressions (Implicit):** Understanding grep's power in pattern matching.  
* **Problem Solving:** Applying filtering techniques to answer specific investigative questions.