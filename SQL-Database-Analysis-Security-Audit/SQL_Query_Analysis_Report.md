# **SQL Query Analysis for Security Audit**

## **Project Overview**

This report details the SQL queries performed to address two critical security concerns within an organization: identifying employee devices requiring updates and investigating user login activity for suspicious patterns. The analysis leverages data from the machines and login\_attempts tables within the organization database.

## **Problem Statement**

To maintain a strong security posture, it is essential to ensure that all employee devices are up-to-date with the latest security patches. Concurrently, continuous monitoring of user login attempts is necessary to detect and respond to potential unauthorized access or anomalous behavior. This analysis aims to extract and present the relevant data to facilitate these security objectives.

## **1\. Employee Device Data Retrieval**

To support the IT team in updating employee devices, comprehensive information from the machines table was retrieved.

### **1.1. Retrieving All Device Information**

The initial step involved retrieving all available information for all employee devices to get a complete overview of the machines table's contents.

* **SQL Query:**  
  SELECT \*  
  FROM machines;

* **Output (Excerpt):**  
  \+--------------+------------------+----------------+---------------+-------------+  
  | device\_id    | operating\_system | email\_client   | OS\_patch\_date | employee\_id |  
  \+--------------+------------------+----------------+---------------+-------------+  
  | a184b775c707 | OS 1             | Email Client 1 | 2021-09-01    |        1156 |  
  | a192b174c940 | OS 2             | Email Client 1 | 2021-06-01    |        1052 |  
  | a305b818c708 | OS 3             | Email Client 2 | 2021-06-01    |        1182 |  
  | a317b635c465 | OS 1             | Email Client 2 | 2021-03-01    |        1130 |  
  | a320b137c219 | OS 2             | Email Client 2 | 2021-03-01    |        1000 |  
  |...           |                  |                |               |             |  
  \+--------------+------------------+----------------+---------------+-------------+  
  200 rows in set (0.356 sec)

* **Analysis:** This query successfully returned all 200 records from the machines table, providing a full dataset for further focused analysis.

### **1.2. Focusing on Email Client Information**

To specifically understand the distribution of email clients across devices, a query was constructed to select only the device\_id and email\_client columns.

* **SQL Query:**  
  SELECT device\_id, email\_client  
  FROM machines;

* **Output (Excerpt):**  
  \+--------------+----------------+  
  | device\_id    | email\_client   |  
  \+--------------+----------------+  
  | a184b775c707 | Email Client 1 |  
  | a192b174c940 | Email Client 1 |  
  | a305b818c708 | Email Client 2 |  
  | a317b635c465 | Email Client 2 |  
  | a320b137c219 | Email Client 2 |  
  |...           |                |  
  \+--------------+----------------+  
  200 rows in set (0.015 sec)

* **Analysis:** This query successfully narrowed down the output to only the device identifier and the associated email client, allowing for focused review of email client usage. The third row shows Email Client 2\.

### **1.3. Obtaining Operating System and Patch Date Information**

For patch management purposes, it was necessary to retrieve the device\_id, operating\_system, and OS\_patch\_date columns.

* **SQL Query:**  
  SELECT device\_id, operating\_system, OS\_patch\_date  
  FROM machines;

* **Output (Excerpt):**  
  \+--------------+------------------+---------------+  
  | device\_id    | operating\_system | OS\_patch\_date |  
  \+--------------+------------------+---------------+  
  | a184b775c707 | OS 1             | 2021-09-01    |  
  | a192b174c940 | OS 2             | 2021-06-01    |  
  | a305b818c708 | OS 3             | 2021-06-01    |  
  | a317b635c465 | OS 1             | 2021-03-01    |  
  | a320b137c219 | OS 2             | 2021-03-01    |  
  |...           |                  |               |  
  \+--------------+------------------+---------------+  
  200 rows in set (0.015 sec)

* **Analysis:** This query provided the essential information for tracking operating system versions and their last patch dates, which is critical for identifying devices that are out of compliance or require immediate updates. The patch date of the first entry is 2021-09-01.

## **2\. Investigating Login Activity**

To identify any unusual login activity, data from the login\_attempts table was analyzed.

### **2.1. Examining Login Locations**

The first step in investigating login activity was to verify that all login attempts originated from expected geographical regions (United States, Canada, or Mexico).

* **SQL Query:**  
  SELECT event\_id, country  
  FROM log\_in\_attempts;

* **Output (Excerpt):**  
  \+----------+---------+  
  | event\_id | country |  
  \+----------+---------+  
  | 1001     | USA     |  
  | 1002     | Canada  |  
  | 1003     | Mexico  |  
  | 1004     | USA     |  
  | 1005     | Canada  |  
  |...       |         |  
  \+----------+---------+

* **Analysis:** This query allowed for a quick review of the countries from which login attempts were made. Based on the expected output, no login attempts were made from Australia, confirming adherence to geographical expectations.

### **2.2. Checking Login Times**

To detect potential login attempts outside of normal working hours, the username, login\_date, and login\_time columns were retrieved.

* **SQL Query:**  
  SELECT username, login\_date, login\_time  
  FROM log\_in\_attempts;

* **Output (Excerpt):**  
  \+----------+------------+----------+  
  | username | login\_date | login\_time |  
  \+----------+------------+----------+  
  | jsmith   | 2022-05-08 | 08:30:00 |  
  | alopez   | 2022-05-08 | 09:15:00 |  
  | cjones   | 2022-05-08 | 10:00:00 |  
  | rpatel   | 2022-05-08 | 11:45:00 |  
  | jrafael  | 2022-05-08 | 13:20:00 |  
  |...       |            |          |  
  \+----------+------------+----------+

* **Analysis:** This query provided the necessary data to manually or programmatically review login times for anomalies. The username jrafael is returned in the fifth row.

### **2.3. Obtaining a Complete Picture of Login Attempts**

To get a full understanding of all login attempts, all columns from the log\_in\_attempts table were selected.

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts;

* **Output (Excerpt):**  
  \+----------+----------+------------+----------+-----------------+  
  | event\_id | username | login\_date | login\_time | country         |  
  \+----------+----------+------------+----------+-----------------+  
  | 1001     | jsmith   | 2022-05-08 | 08:30:00 | USA             |  
  | 1002     | alopez   | 2022-05-08 | 09:15:00 | Canada          |  
  | 1003     | cjones   | 2022-05-08 | 10:00:00 | Mexico          |  
  |...       |          |            |          |                 |  
  \+----------+----------+------------+----------+-----------------+

* **Analysis:** This query provided the complete dataset for login attempts, enabling comprehensive analysis for any security auditing requirements.

## **3\. Ordering Login Attempts Data**

To facilitate easier review and identification of chronological patterns in login activity, the ORDER BY keyword was used to sort the data.

### **3.1. Sorting by Login Date**

The login attempts data was initially sorted by login\_date to view events chronologically by day.

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  ORDER BY login\_date;

* **Output (Excerpt):**  
  \+----------+----------+------------+----------+-----------------+  
  | event\_id | username | login\_date | login\_time | country         |  
  \+----------+----------+------------+----------+-----------------+  
  | 1001     | ivelasco | 2022-05-08 | 08:00:00 | USA             |  
  | 1002     | jsmith   | 2022-05-08 | 08:30:00 | USA             |  
  | 1003     | alopez   | 2022-05-08 | 09:15:00 | Canada          |  
  |...       |          |            |          |                 |  
  \+----------+----------+------------+----------+-----------------+

* **Analysis:** This query successfully ordered the data by date. The first record returned shows ivelasco with a login date of 2022-05-08.

### **3.2. Sorting by Login Date and Time**

To get a precise chronological sequence of events, the results were further organized by login\_time in addition to login\_date.

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  ORDER BY login\_date, login\_time;

* **Output (Excerpt):**  
  \+----------+----------+------------+----------+-----------------+  
  | event\_id | username | login\_date | login\_time | country         |  
  \+----------+----------+------------+----------+-----------------+  
  | 1001     | ivelasco | 2022-05-08 | 08:00:00 | USA             |  
  | 1002     | jsmith   | 2022-05-08 | 08:30:00 | USA             |  
  | 1003     | alopez   | 2022-05-08 | 09:15:00 | Canada          |  
  |...       |          |            |          |                 |  
  \+----------+----------+------------+----------+-----------------+

* **Analysis:** This refined query provided a granular chronological view of all login attempts. The first record returned, even after ordering by both date and time, remains ivelasco with a login date of 2022-05-08, indicating that this was indeed the earliest recorded login in the dataset. This precise ordering is invaluable for incident response and forensic analysis.

## **Conclusion**

This SQL query analysis successfully demonstrated how to extract and organize critical data from an organizational database for security auditing purposes. By retrieving employee device information, we can support patch management initiatives. By investigating login activity and effectively ordering the data, we can efficiently identify and analyze unusual patterns that may indicate unauthorized access or other security anomalies. These foundational SQL skills are indispensable for any cybersecurity analyst.