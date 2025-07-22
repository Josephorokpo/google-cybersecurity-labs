# **SQL Relational Data Joining for Security Incident Investigation**

## **Project Introduction**

This repository contains a practical project demonstrating the application of SQL JOIN operations, a fundamental skill for cybersecurity analysts working with relational databases. In security investigations, data relevant to an incident often spans across multiple tables. The ability to effectively combine these disparate datasets is crucial for gaining a holistic view, identifying relationships between entities (like users and their devices), and uncovering anomalies.

## **Scenario**

The project addresses a simulated security incident involving compromised machines. As a security analyst, my role was to extract and correlate necessary information from the machines, employees, and log\_in\_attempts tables within an organizational database to support the investigation.

## **Objectives**

The primary objectives of this analysis were to:

1. **Identify which employees are using which machines** by performing an INNER JOIN.  
2. **Find machines not assigned to any specific user** and **users not assigned to any specific machine** using LEFT JOIN and RIGHT JOIN respectively, to uncover unmanaged assets or orphaned accounts.  
3. **List all login attempts made by all employees** by performing an INNER JOIN between employee and login data.

## **Tools and Technologies**

* **Database System:** MariaDB  
* **Language:** SQL (Structured Query Language)

## **Analysis and Findings**

The analysis involved constructing and executing various SQL queries, leveraging different types of JOINs to connect related tables. The findings from each query provided critical insights into the relationships between employees, their devices, and their login activities, directly aiding the security incident investigation.

A detailed report of the analysis, including all queries and their outputs, is available in the SQL\_Join\_Analysis\_Report.md file.

## **Key Learnings**

This project provided valuable hands-on experience in:

* **Understanding Relational Databases:** Recognizing how tables are interconnected via common columns.  
* **INNER JOIN:** Combining rows from two tables based on a matching column, useful for direct correlations.  
* **LEFT JOIN:** Retrieving all records from the "left" table and matching records from the "right" table, valuable for identifying unmatched entities (e.g., machines without assigned users).  
* **RIGHT JOIN:** Retrieving all records from the "right" table and matching records from the "left" table, useful for identifying unmatched entities (e.g., users without assigned machines).  
* **Security Incident Support:** Applying SQL JOINs to gather comprehensive data for forensic analysis and incident response.