# **Linux File Management Lab Report**

## **Activity Overview**

This lab activity provided practical experience in using Linux commands to modify a directory structure and the files it contains. It also covered using the nano text editor to add text to a file. These skills are fundamental for security analysts to organize data, detect issues, and maintain data safety in Linux environments.

## **Scenario Execution**

The objective was to reorganize the /home/analyst directory to a new, optimized structure. The lab started with the analyst user logged into the Bash shell.

**Initial Directory Structure:**

home  
└── analyst  
    ├── notes  
    │   ├── Q3patches.txt  
    │   └── tempnotes.txt  
    ├── reports  
    │   ├── Q1patches.txt  
    │   └── Q2patches.txt  
    └── temp

**Target Directory Structure:**

home  
└── analyst  
    ├── logs  
    ├── notes  
    │   └── tasks.txt      
    └── reports  
        ├── Q1patches.txt  
        └── Q2patches.txt  
        └── Q3patches.txt

### **Task 1: Create a new directory**

First, I created a dedicated subdirectory called logs, which will be used to store all future log files.

* **Objective** 1: Create a new subdirectory called logs in the /home/analyst **directory.**  
  * **Command:**  
    mkdir logs

  * **Output (implied):** No direct output on success.  
* **Objective 2: List the contents of the /home/analyst** directory **to confirm that you’ve successfully created the new logs subdirectory.**  
  * **Command:**  
    ls

  * **Output:**  
    logs  notes  reports  temp

  * **Verification:** The logs directory is now listed, confirming its creation.

### **Task 2: Remove a directory**

Next, I removed the temp directory, as it was no longer needed.

* **Objective 1: Remove the /home/analyst/temp directory.**  
  * **Command:**  
    rmdir temp

  * **Output (implied):** No direct output on success.  
* **Objective 2: List the contents of the /home/analyst directory to confirm that you have removed the temp subdirectory.**  
  * **Command:**  
    ls

  * **Output:**  
    logs  notes  reports

  * **Verification:** The temp directory is no longer listed, confirming its removal.

### **Task 3: Move a file**

The Q3patches.txt file contained notes taken on third-quarter patches and needed to be moved from the notes directory to the reports directory.

* **Objective 1: Navigate to the /home/analyst/notes directory.**  
  * **Command (using absolute path):**  
    cd /home/analyst/notes

  * *(Alternatively, using relative path from /home/analyst):*  
    cd notes

  * **Output (implied):** Current directory changes to /home/analyst/notes.  
* **Objective** 2: Move the **Q3patches.txt file from the /home/analyst/notes directory to the /home/analyst/reports directory.**  
  * **Command:**  
    mv Q3patches.txt /home/analyst/reports/

  * **Output (implied):** No direct output on success.  
* **Objective 3: List the contents of the /home/analyst/reports directory to confirm that you have moved the file successfully.**  
  * **Command:**  
    ls /home/analyst/reports

  * **Output:**  
    Q1patches.txt  Q2patches.txt  Q3patches.txt

  * **Verification:** All three quarterly patch files are now listed in the reports directory.

### **Task 4: Remove a file**

Next, I deleted an unused file called tempnotes.txt from the /home/analyst/notes directory.

* **Objective 1: Remove the tempnotes.txt file from the /home/analyst/notes directory.**  
  * **Command:**  
    rm tempnotes.txt

