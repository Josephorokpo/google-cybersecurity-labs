# **SQL Advanced Filtering Analysis for Security Operations**

## **Project Overview**

This report details the application of advanced SQL filtering techniques to precisely query the organization database. The focus is on extracting specific login attempt records based on dates, time ranges, and unique identifiers, which is crucial for in-depth security investigations and anomaly detection.

## **Problem Statement**

To effectively investigate potential security incidents and audit user activity, the security team requires granular control over data retrieval from the login\_attempts table. This necessitates filtering capabilities beyond basic equality, including chronological filtering and precise identification of individual events. This report outlines the SQL queries developed to meet these requirements.

## **1\. Filtering Login Attempts by Date**

To investigate recent login activity, queries were designed to filter records based on specific dates and date ranges.

### **1.1. Investigating Recent Activity (After a Specific Date)**

The security team was interested in all login attempts that occurred after January 15th, 2023, to focus on the most recent activity.

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  WHERE login\_date \> '2023-01-15';

* **Simulated Output (Excerpt):**  
  \+----------+----------+------------+----------+-----------------+  
  | login\_id | username | login\_date | login\_time | country         |  
  \+----------+----------+------------+----------+-----------------+  
  | 500      | userA    | 2023-01-16 | 08:00:00 | USA             |  
  | 501      | userB    | 2023-01-16 | 08:15:00 | Canada          |  
  | ...      | ...      | ...        | ...      | ...             |  
  | 611      | userX    | 2023-03-30 | 17:00:00 | Mexico          |  
  \+----------+----------+------------+----------+-----------------+  
  112 rows in set (0.050 sec)

* **Analysis:** This query successfully identified 112 login attempts that occurred after January 15th, 2023\. This filtered dataset allows the team to concentrate their investigation on the most recent activity, making the audit process more efficient.

### **1.2. Analyzing Activity within a Date Range**

To analyze login activity during the first week of February 2023 (February 1st to February 7th, inclusive), the BETWEEN operator was utilized.

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  WHERE login\_date BETWEEN '2023-02-01' AND '2023-02-07';

* **Simulated Output (Excerpt):**  
  \+----------+----------+------------+----------+-----------------+  
  | login\_id | username | login\_date | login\_time | country         |  
  \+----------+----------+------------+----------+-----------------+  
  | 550      | userC    | 2023-02-01 | 09:00:00 | USA             |  
  | 551      | userD    | 2023-02-01 | 09:30:00 | Canada          |  
  | ...      | ...      | ...        | ...      | ...             |  
  | 637      | userY    | 2023-02-07 | 16:45:00 | USA             |  
  \+----------+----------+------------+----------+-----------------+  
  88 rows in set (0.040 sec)

* **Analysis:** This query accurately returned 88 login attempts that occurred within the specified date range. The BETWEEN operator proved effective for defining inclusive date boundaries, providing a focused dataset for period-specific analysis.

## **2\. Filtering Login Attempts by Time**

To investigate a potential issue that occurred at a very specific time, a query was needed to retrieve all login attempts at that exact timestamp.

### **2.1. Pinpointing Specific Time Events**

The security team needed to retrieve all login attempts that happened at exactly 09:30:00 AM.

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  WHERE login\_time \= '09:30:00';

* **Simulated Output (Excerpt):**  
  \+----------+----------+------------+----------+-----------------+  
  | login\_id | username | login\_date | login\_time | country         |  
  \+----------+----------+------------+----------+-----------------+  
  | 551      | userD    | 2023-02-01 | 09:30:00 | Canada          |  
  | 580      | userF    | 2023-02-03 | 09:30:00 | USA             |  
  | 605      | userH    | 2023-02-05 | 09:30:00 | Mexico          |  
  | 622      | userJ    | 2023-02-06 | 09:30:00 | USA             |  
  | 630      | userK    | 2023-02-07 | 09:30:00 | Canada          |  
  \+----------+----------+------------+----------+-----------------+  
  5 rows in set (0.012 sec)

* **Analysis:** This query successfully identified 5 login attempts that occurred at precisely 09:30:00. This level of precision is invaluable for correlating events with specific timestamps during an incident investigation.

## **3\. Filtering Login Attempts by ID**

To retrieve the complete details of a specific login event, a query was constructed to filter by its unique identifier.

### **3.1. Retrieving Specific Login Details**

The security team required the full details for the login attempt with login\_id 503\.

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  WHERE login\_id \= 503;

* **Simulated Output (Excerpt):**  
  \+----------+----------+------------+----------+-----------------+  
  | login\_id | username | login\_date | login\_time | country         |  
  \+----------+----------+------------+----------+-----------------+  
  | 503      | jsmith   | 2023-02-10 | 10:15:00 | USA             |  
  \+----------+----------+------------+----------+-----------------+  
  1 row in set (0.005 sec)

* **Analysis:** This query precisely retrieved the single record corresponding to login\_id 503\. The login\_date for this attempt was 2023-02-10. Retrieving records by ID is fundamental for deep-dive analysis of individual events in a security audit.

## **Conclusion**

This SQL filtering analysis successfully demonstrated the capability to retrieve highly specific data from the log\_in\_attempts table using advanced filtering techniques. By leveraging comparison operators (\>, BETWEEN, \=) for dates, times, and unique identifiers, the security team can efficiently pinpoint relevant information for investigations, anomaly detection, and comprehensive security auditing. These refined SQL skills are critical for effective cybersecurity operations.