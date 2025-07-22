# **SQL Join Analysis for Security Incident Investigation**

## **Project Overview**

This report details the application of SQL JOIN operations to correlate data from multiple tables within an organizational database. This analysis was conducted as part of a security incident investigation concerning compromised machines, aiming to link employee, machine, and login attempt information for a holistic view of the incident.

## **Problem Statement**

In a security incident, critical information is often distributed across various database tables. To effectively investigate the compromise of machines, it is essential to combine data from the machines table (device details), employees table (employee information), and log\_in\_attempts table (user login activity). This report outlines the SQL queries used to perform these necessary data correlations.

## **1\. Matching Employees to Their Machines**

To identify which employees are using which machines, an INNER JOIN was performed between the machines and employees tables using the common device\_id column.

* **Initial Query (for context):**  
  SELECT \*  
  FROM machines;

  * **Analysis:** This initial query retrieves all records from the machines table, but it does not provide employee-specific information, highlighting the need for a join.  
* **SQL Query (Inner Join):**  
  SELECT \*  
  FROM machines  
  INNER JOIN employees ON machines.device\_id \= employees.device\_id;

* **Output (Excerpt):**  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  | device\_id    | operating\_system | email\_client   | OS\_patch\_date | employee\_id | employee\_id | username | department | office    | phone\_extension |  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  | a184b775c707 | OS 1             | Email Client 1 | 2021-09-01    |        1156 |        1156 | jsmith   | IT         | North-101 | 5001            |  
  | a192b174c940 | OS 2             | Email Client 1 | 2021-06-01    |        1052 |        1052 | alopez   | Sales      | East-201  | 6001            |  
  | a305b818c708 | OS 3             | Email Client 2 | 2021-06-01    |        1182 |        1182 | cjones   | Marketing  | West-301  | 7001            |  
  |...           |                  |                |               |             |             |          |            |           |                 |  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  185 rows in set (0.045 sec)

* **Analysis:** The INNER JOIN successfully combined records from both tables where the device\_id matched, returning 185 rows. This query provides a direct correlation between employees and their assigned machines, which is crucial for identifying the users potentially affected by compromised devices.

## **2\. Returning More Data (Left and Right Joins)**

To gain a more complete picture, including entities that might not have a direct match, LEFT JOIN and RIGHT JOIN were utilized. This helps in identifying unassigned assets or users without assigned resources.

### **2.1. Including All Machines (Left Join)**

This query aimed to return information on all machines, regardless of whether they are currently assigned to an employee.

* **SQL Query (Left Join):**  
  SELECT \*  
  FROM machines  
  LEFT JOIN employees ON machines.device\_id \= employees.device\_id;

* **Output (Excerpt):**  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  | device\_id    | operating\_system | email\_client   | OS\_patch\_date | employee\_id | employee\_id | username | department | office    | phone\_extension |  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  | a184b775c707 | OS 1             | Email Client 1 | 2021-09-01    |        1156 |        1156 | jsmith   | IT         | North-101 | 5001            |  
  | a192b174c940 | OS 2             | Email Client 1 | 2021-06-01    |        1052 |        1052 | alopez   | Sales      | East-201  | 6001            |  
  | ...          | ...              | ...            | ...           | ...         | ...         | ...      | ...        | ...       | ...             |  
  | z999y888x777 | OS 4             | Email Client 3 | 2022-01-01    |        NULL |        NULL | NULL     | NULL       | NULL      | NULL            |  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  200 rows in set (0.050 sec)

* **Analysis:** The LEFT JOIN returned all records from the machines table (the "left" table), including those without a matching employee\_id in the employees table. For unmatched machines, the employee columns showed NULL values. This is valuable for identifying unassigned or spare machines that might still require security updates or inventory management. The last username returned is NULL.

### **2.2. Including All Employees (Right Join)**

Conversely, this query aimed to retrieve information on all employees, including those who may not currently have an assigned machine.

* **SQL Query (Right Join):**  
  SELECT \*  
  FROM machines  
  RIGHT JOIN employees ON machines.device\_id \= employees.device\_id;

* **Output (Excerpt):**  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  | device\_id    | operating\_system | email\_client   | OS\_patch\_date | employee\_id | employee\_id | username | department | office    | phone\_extension |  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  | a184b775c707 | OS 1             | Email Client 1 | 2021-09-01    |        1156 |        1156 | jsmith   | IT         | North-101 | 5001            |  
  | a192b174c940 | OS 2             | Email Client 1 | 2021-06-01    |        1052 |        1052 | alopez   | Sales      | East-201  | 6001            |  
  | ...          | ...              | ...            | ...           | ...         | ...         | ...      | ...        | ...       | ...             |  
  | NULL         | NULL             | NULL           | NULL          |        1200 |        1200 | areyes   | HR         | West-400  | 8001            |  
  \+--------------+------------------+----------------+---------------+-------------+-------------+----------+------------+-----------+-----------------+  
  200 rows in set (0.055 sec)

* **Analysis:** The RIGHT JOIN returned all records from the employees table (the "right" table), including those without a matching device\_id in the machines table. For unmatched employees, the machines columns showed NULL values. This is useful for identifying employees who might be new, on leave, or have not yet been assigned a device, ensuring all personnel are accounted for. The last username returned is areyes.

## **3\. Retrieving Login Attempt Data**

To continue investigating the security incident, information on all employees who have made login attempts was required. This was achieved by performing an INNER JOIN on the employees and log\_in\_attempts tables, linking them on the common username column.

* **SQL Query (Inner Join):**  
  SELECT \*  
  FROM employees  
  INNER JOIN log\_in\_attempts ON employees.username \= log\_in\_attempts.username;

* **Output (Excerpt):**  
  \+-------------+----------+------------+-----------+-----------------+----------+------------+----------+---------+---------+  
  | employee\_id | username | department | office    | phone\_extension | login\_id | login\_date | login\_time | country | success |  
  \+-------------+----------+------------+-----------+-----------------+----------+------------+----------+---------+---------+  
  | 1156        | jsmith   | IT         | North-101 | 5001            | 1001     | 2022-05-08 | 08:30:00 | USA     | 1       |  
  | 1052        | alopez   | Sales      | East-201  | 6001            | 1002     | 2022-05-08 | 09:15:00 | Canada  | 1       |  
  | 1182        | cjones   | Marketing  | West-301  | 7001            | 1003     | 2022-05-08 | 10:00:00 | Mexico  | 1       |  
  |...          |          |            |           |                 |...       |            |          |         |         |  
  \+-------------+----------+------------+-----------+-----------------+----------+------------+----------+---------+---------+  
  200 rows in set (0.060 sec)

* **Analysis:** This INNER JOIN successfully returned 200 records, combining employee details with their corresponding login attempts. This comprehensive view is invaluable for security investigations, allowing analysts to quickly link login events to specific employees and their departmental/office context, aiding in anomaly detection and forensic analysis.

## **Conclusion**

This SQL analysis demonstrated the critical role of different JOIN types (INNER, LEFT, RIGHT) in effectively combining data from multiple relational tables. By leveraging these operations, I was able to correlate employee information with machine assignments and login activities, providing a holistic dataset essential for security incident investigations, asset management, and user behavior analysis. This expertise in SQL JOINs is fundamental for any cybersecurity analyst.