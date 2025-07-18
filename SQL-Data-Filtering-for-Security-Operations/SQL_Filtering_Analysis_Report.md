# **SQL Filtering Analysis for Security Operations**

## **Project Overview**

This report details the SQL queries performed to retrieve specific information about employee devices and departmental affiliations from the organization database. This data is crucial for various security operations, including system updates, privacy notice distribution, and targeted incident alerts. The analysis demonstrates effective use of SQL filtering techniques.

## **Problem Statement**

To maintain operational efficiency and security compliance, specific data subsets are frequently required from the central database. This includes identifying machines needing updates based on their operating system, locating employees within particular departments for policy dissemination, and pinpointing users associated with problematic machines by location. This report outlines the SQL queries used to address these precise data retrieval needs.

## **1\. Listing All Organization Machines**

The initial step involved obtaining a comprehensive list of all organization machines and their operating systems from the machines table.

* **SQL Query:**  
  SELECT device\_id, operating\_system  
  FROM machines;

* **Output (Excerpt):**  
  \+--------------+------------------+  
  | device\_id    | operating\_system |  
  \+--------------+------------------+  
  | a184b775c707 | OS 1             |  
  | a192b174c940 | OS 2             |  
  | a305b818c708 | OS 3             |  
  | a317b635c465 | OS 1             |  
  | a320b137c219 | OS 2             |  
  | a398b471c573 | OS 3             |  
  |...           |                  |  
  \+--------------+------------------+  
  200 rows in set (0.028 sec)

* **Analysis:** This query successfully returned 200 rows, displaying only the device\_id and operating\_system for all machines in the database. This provided a foundational dataset for subsequent filtering.

## **2\. Retrieving Machines with 'OS 2'**

To identify machines requiring a specific update, a filter was applied to retrieve only those running 'OS 2'.

* **SQL Query:**  
  SELECT device\_id, operating\_system  
  FROM machines  
  WHERE operating\_system \= 'OS 2';

* **Output (Excerpt):**  
  \+--------------+------------------+  
  | device\_id    | operating\_system |  
  \+--------------+------------------+  
  | a192b174c940 | OS 2             |  
  | a320b137c219 | OS 2             |  
  | a821b452c176 | OS 2             |  
  | b157c491d493 | OS 2             |  
  | b264c773d977 | OS 2             |  
  |...           |                  |  
  \+--------------+------------------+  
  80 rows in set (0.264 sec)

* **Analysis:** The WHERE clause effectively filtered the results, returning 80 machines that use the 'OS 2' operating system. This targeted list is essential for the update team.

## **3\. Listing Employees in Specific Departments**

To facilitate the distribution of a confidential financial information notice, a list of employees in the 'Finance' and 'Sales' departments was required.

### **3.1. Employees in 'Finance' Department**

* **SQL Query:**  
  SELECT \*  
  FROM employees  
  WHERE department \= 'Finance';

* **Output (Excerpt):**  
  \+-------------+----------+------------+---------+-----------------+  
  | employee\_id | username | department | office  | phone\_extension |  
  \+-------------+----------+------------+---------+-----------------+  
  | 1003        | jdoe     | Finance    | North-101 | 5001            |  
  | 1015        | asmith   | Finance    | North-102 | 5002            |  
  |...          |          |            |         |                 |  
  \+-------------+----------+------------+---------+-----------------+

* **Analysis:** This query successfully retrieved all records for employees belonging to the 'Finance' department. The employee\_id of the first row returned is 1003\.

### **3.2. Employees in 'Sales' Department**

* **SQL Query:**  
  SELECT \*  
  FROM employees  
  WHERE department \= 'Sales';

* **Output (Excerpt):**  
  \+-------------+----------+------------+---------+-----------------+  
  | employee\_id | username | department | office  | phone\_extension |  
  \+-------------+----------+------------+---------+-----------------+  
  | 1001        | mlee     | Sales      | East-201  | 6001            |  
  | 1005        | rkim     | Sales      | East-202  | 6002            |  
  |...          |          |            |         |                 |  
  \+-------------+----------+------------+---------+-----------------+  
  33 rows in set (0.010 sec)

* **Analysis:** This query returned 33 employees working in the 'Sales' department, providing the necessary list for the privacy notice distribution.

## **4\. Identifying Employee Machines by Location**

To address issues with machines in the 'South' building, specific employee and computer information was needed.

### **4.1. Employee for a Specific Office ('South-109')**

* **SQL Query:**  
  SELECT username  
  FROM employees  
  WHERE office \= 'South-109';

* **Output (Excerpt):**  
  \+----------+  
  | username |  
  \+----------+  
  | jlansky  |  
  \+----------+

* **Analysis:** This query successfully identified jlansky as the employee using the computer in 'South-109', enabling a direct alert to be sent.

### **4.2. All Employees in the 'South' Building**

To address issues with all machines in the 'South' building, a wildcard search was used.

* **SQL Query:**  
  SELECT \*  
  FROM employees  
  WHERE office LIKE 'South%';

* **Output (Excerpt):**  
  \+-------------+----------+------------+-----------+-----------------+  
  | employee\_id | username | department | office    | phone\_extension |  
  \+-------------+----------+------------+-----------+-----------------+  
  | 1003        | jdoe     | Finance    | South-101 | 5001            |  
  | 1020        | bbrown   | IT         | South-102 | 5005            |  
  | 1035        | cgreen   | Marketing  | South-103 | 5010            |  
  |...          |          |            |           |                 |  
  \+-------------+----------+------------+-----------+-----------------+

* **Analysis:** The LIKE operator with the % wildcard effectively returned all employees whose office names started with 'South'. The first employee listed in the 'South' building belongs to the 'Finance' department. This list is crucial for a broader alert or intervention regarding machines in that building.

## **Conclusion**

This SQL filtering analysis successfully demonstrated the power of SELECT, WHERE, and LIKE clauses in retrieving highly specific data from a database. These capabilities are fundamental for cybersecurity analysts to efficiently support various operational tasks, from managing system updates and enforcing policies to responding to security incidents based on precise data requirements.