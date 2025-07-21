# **SQL Complex Filtering for Security Audit**

## **Project Introduction**

This repository contains a practical project demonstrating the application of advanced SQL logical operators (AND, OR, NOT) for complex data filtering. As a security analyst, the ability to combine multiple filtering conditions is crucial for precise data retrieval, enabling targeted investigations into security issues and efficient management of organizational assets. This project focuses on extracting specific information about employees, machines, and login activities from a database.

## **Scenario**

The security team requires highly specific information from the organizational database to investigate potential security issues and facilitate computer updates. This involves retrieving data based on combinations of criteria, such as login times, dates, geographical locations, and departmental affiliations.

## **Objectives**

The primary objectives of this analysis were to:

1. **Retrieve all failed login attempts after business hours** for immediate investigation.  
2. **Identify login attempts that occurred on specific dates** to analyze suspicious events.  
3. **Filter for login attempts not originating from a specific country** (Mexico) to detect unusual access locations.  
4. **Obtain information on employees in specific departments and office locations** (Marketing in East building) for targeted updates.  
5. **Retrieve information on employees in a set of departments** (Finance or Sales) for policy-related updates.  
6. **Identify all employees not belonging to a specific department** (Information Technology) for broader updates.

## **Tools and Technologies**

* **Database System:** MariaDB  
* **Language:** SQL (Structured Query Language)

## **Analysis and Findings**

The analysis involved constructing and executing various SQL queries against the organization database, leveraging AND, OR, NOT, and LIKE operators to combine and negate filtering conditions. The findings from each query provided precise datasets for the security team's operational needs.

A detailed report of the analysis, including all queries and their outputs, is available in the SQL\_Complex\_Filtering\_Analysis\_Report.md file.

## **Key Learnings**

This project provided valuable hands-on experience in:

* **Logical Operators (AND, OR, NOT):** Combining and negating multiple filtering conditions.  
* **Date and Time Filtering:** Applying WHERE clauses with time and Boolean values.  
* **String Pattern Matching with Negation:** Using NOT LIKE for excluding specific patterns.  
* **Multi-Criteria Data Retrieval:** Constructing complex queries to meet specific business and security requirements.  
* **Practical Security Applications:** Enhancing efficiency in security audits, incident response, and asset management through advanced SQL filtering.