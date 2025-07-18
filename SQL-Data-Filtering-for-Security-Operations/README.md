# **SQL Data Filtering for Security Operations**

## **Project Introduction**

This repository contains a practical project demonstrating the application of SQL for targeted data retrieval, a critical skill for cybersecurity analysts. In security operations, the ability to quickly filter and extract specific information from large datasets is essential for tasks such as identifying systems needing updates, enforcing policy compliance, and responding to incidents. This project focuses on using SQL's WHERE and LIKE clauses to efficiently locate relevant employee and machine data.

## **Scenario**

The scenario involves a need to obtain specific information about employees, their machines, and their departments to support various organizational tasks. These tasks include running system updates, posting privacy notices in specific departments, and sending alerts to employees about machine issues. The required data resides in the machines and employees tables within the organization database.

## **Objectives**

The primary objectives of this analysis were to:

1. **List all organization machines** and their operating systems.  
2. **Retrieve a filtered list of machines** running a specific operating system (OS 2\) for update purposes.  
3. **Identify employees in specific departments** (Finance and Sales) for policy communication.  
4. **Locate employee and machine information** based on office location to facilitate incident response for machine issues.

## **Tools and Technologies**

* **Database System:** MariaDB  
* **Language:** SQL (Structured Query Language)

## **Analysis and Findings**

The analysis involved constructing and executing various SQL queries against the organization database, progressively applying filters to refine the results. The findings from each query directly addressed the operational needs outlined in the scenario.

A detailed report of the analysis, including all queries and their outputs, is available in the SQL_Filtering_Analysis_Report.md file.

## **Key Learnings**

This project provided valuable hands-on experience in:

* **Basic SQL Filtering:** Using the WHERE clause with equality (=) to narrow down results.  
* **String Matching:** Employing the LIKE operator with the wildcard character (%) for flexible pattern matching.  
* **Targeted Data Retrieval:** Efficiently extracting specific subsets of data from tables.  
* **Practical Security Applications:** Applying SQL skills to real-world security operations tasks such as patch management, compliance, and incident response.
