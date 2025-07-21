# **SQL Advanced Filtering for Security Analysis**

## **Project Introduction**

This repository contains a practical project demonstrating the application of advanced SQL filtering techniques to extract precise information from a database. As a security analyst, the ability to refine data retrieval based on specific dates, times, and unique identifiers is crucial for in-depth investigations, anomaly detection, and targeted security analysis. This project utilizes common SQL operators and clauses to achieve granular data filtering.

## **Scenario**

Continuing work with an organizational database, the security team requires more precise information from the login\_attempts logs and machines table. This includes retrieving records based on specific time frames and individual login identifiers to investigate user login activity and identify devices needing updates.

## **Objectives**

The primary objectives of this analysis were to:

1. **Filter for login attempts made after a certain date** to investigate recent activity.  
2. **Filter for login attempts made within a specific date range** for focused analysis of activity during a particular period.  
3. **Filter for login attempts made at an exact time** to pinpoint events around a specific timestamp.  
4. **Filter for login attempts by their unique ID** to retrieve details of individual login events.

## **Tools and Technologies**

* **Database System:** MariaDB  
* **Language:** SQL (Structured Query Language)

## **Analysis and Findings**

The analysis involved constructing and executing various SQL queries against the organization database, progressively applying more refined filters. The findings from each query provided targeted insights into user login patterns and device statuses, directly supporting security investigation needs.

A detailed report of the analysis, including all queries and their outputs, is available in the SQL\_Advanced\_Filtering\_Analysis\_Report.md file.

## **Key Learnings**

This project provided valuable hands-on experience in:

* **Date and Time Filtering:** Using comparison operators (\>, \>=, \<, \<=) and the BETWEEN operator for date and time ranges.  
* **Exact Value Matching:** Filtering records based on precise string or numeric values using the equality operator (=).  
* **Targeted Investigation:** Applying SQL filters to efficiently narrow down large datasets for security investigations.  
* **MariaDB Querying:** Practical experience with MariaDB's SQL syntax for data retrieval.