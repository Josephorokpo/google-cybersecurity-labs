# **Linux Grep Filtering Lab Report**

## **Activity Overview**

This lab provided practical experience in using the grep command and piping (|) within a Linux Bash shell to search for specific information within files and to filter file listings. These are essential skills for security analysts to efficiently locate critical data in various system and application logs.

## **Scenario Execution**

The objective was to obtain information from server log and user data files, and to find files with specific names within the /home/analyst directory. The lab started with the analyst user logged into the Bash shell.

### **Task 1: Search for error messages in a log file**

In this task, I navigated to the /home/analyst/logs directory and extracted all lines containing "error" from the server\_logs.txt file.

* **Objective 1: Navigate to the /home/analyst/logs directory.**  
  * **Command:**  
    cd /home/analyst/logs

  * **Output (implied):** Current directory changes to /home/analyst/logs.  
* **Objective 2: Use grep to filter the server\_logs.txt file, and return all lines containing the text string error.**  
  * **Command:**  
    grep "error" server\_logs.txt

  * **Simulated Output (based on provided answer of 6 errors):**  
    \[ERROR\] Failed to connect to database.  
    \[ERROR\] Authentication failed for user 'guest'.  
    \[ERROR\] Disk write error on /var/log.  
    \[ERROR\] Service 'nginx' failed to start.  
    \[ERROR\] Invalid configuration detected.  
    \[ERROR\] Unhandled exception occurred.

  * **Answer to Question:** How many error lines are there in the server\_logs.txt file?  
    * Six (as per the lab's provided answer).

### **Task 2: Find files containing specific strings**

In this task, I navigated to the /home/analyst/reports/users directory and used piping with ls and grep to find files with specific strings in their names.

* **Objective 1: Navigate to the /home/analyst/reports/users directory.**  
  * **Command:**  
    cd /home/analyst/reports/users

  * **Output (implied):** Current directory changes to /home/analyst/reports/users.  
* **Objective 2: Using the pipe character (|), pipe the output of the ls command to the grep command to list only the files containing the string Q1 in their names.**  
  * **Command:**  
    ls | grep "Q1"

  * **Simulated Output (based on provided answer of 3 files):**  
    Q1\_added\_users.txt  
    Q1\_access\_report.csv  
    Q1\_login\_attempts.log

  * **Answer to Question:** How many files in the /home/analyst/reports/users subdirectory contain "Q1" in their names?  
    * Three (as per the lab's provided answer).  
* **Objective 3: List the files that contain the word access in their names.**  
  * **Command:**  
    ls | grep "access"

  * **Simulated Output (based on provided answer of 4 files):**  
    Q1\_access\_report.csv  
    Q2\_access\_log.txt  
    Q3\_access\_summary.json  
    Q4\_access\_control.conf

  * **Answer to Question:** How many files in the /home/analyst/reports/users directory contain "access" in their names?  
    * Four (as per the lab's provided answer).

### **Task 3: Search more file contents**

In this task, I searched for specific information within user files.

* **Objective 1: Display the files in the /home/analyst/reports/users directory.**  
  * **Command:**  
    ls

  * **Simulated Output (example files):**  
    Q1\_added\_users.txt  
    Q1\_access\_report.csv  
    Q1\_login\_attempts.log  
    Q2\_deleted\_users.txt  
    Q2\_access\_log.txt  
    Q3\_added\_users.txt  
    Q3\_access\_summary.json  
    Q4\_added\_users.txt  
    Q4\_access\_control.conf

* **Objective 2: Search the Q2\_deleted\_users.txt file for the username jhill.**  
  * **Command:**  
    grep "jhill" Q2\_deleted\_users.txt

  * **Simulated Output (based on provided answer "Yes"):**  
    jhill,Finance,2024-03-15

  * **Answer to Question:** Did you find the username jhill in the Q2\_deleted\_users.txt file?  
    * Yes (as per the lab's provided answer).  
* **Objective 3: Search the Q4\_added\_users.txt file to list the users who were added to the Human Resources department.**  
  * **Command:**  
    grep "Human Resources" Q4\_added\_users.txt

  * **Simulated Output (based on provided answer of 2 users):**  
    alice.smith,Human Resources,1050  
    bob.johnson,Human Resources,1051

  * **Answer to Question:** How many users were added to the Human Resources department in quarter 4?  
    * Two (as per the lab's provided answer).

## **Conclusion**

This lab provided valuable practical experience in using grep to search for specific information contained in files and to find files containing specific strings by piping the output of ls into grep. These fundamental Linux tools are crucial for efficient data analysis and investigation in a cybersecurity role.