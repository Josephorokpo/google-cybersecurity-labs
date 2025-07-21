# **SQL Complex Filtering Analysis for Security Operations**

## **Project Overview**

This report details the application of advanced SQL filtering techniques using logical operators (AND, OR, NOT) to extract highly specific information from the organization database. The analysis focuses on retrieving targeted data related to employee machines and login activities, which is critical for investigating security issues and managing system updates.

## **Problem Statement**

The security team requires precise data subsets from the database to investigate potential security incidents and facilitate computer updates. This involves complex filtering based on multiple criteria, including login times, dates, geographical origins, and departmental affiliations. This report outlines the SQL queries developed to meet these intricate data retrieval requirements.

## **1\. Retrieving After-Hours Failed Login Attempts**

To investigate suspicious activity, the security team needed to identify all unsuccessful login attempts that occurred after business hours (18:00).

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  WHERE login\_time \> '18:00' AND success \= FALSE;

* **Simulated Output (Excerpt):**  
  \+----------+----------+------------+----------+---------+---------+  
  | login\_id | username | login\_date | login\_time | country | success |  
  \+----------+----------+------------+----------+---------+---------+  
  | 105      | userX    | 2023-03-10 | 19:15:00 | USA     | 0       |  
  | 112      | userY    | 2023-03-11 | 20:00:00 | Canada  | 0       |  
  | ...      | ...      | ...        | ...      | ...     | ...     |  
  | 123      | userZ    | 2023-03-12 | 22:30:00 | Mexico  | 0       |  
  \+----------+----------+------------+----------+---------+---------+  
  19 rows in set (0.030 sec)

* **Analysis:** This query successfully identified 19 failed login attempts that occurred after 18:00. The AND operator effectively combined the time and success status criteria, providing a focused list for investigation into potential unauthorized access attempts outside of normal working hours.

## **2\. Retrieving Login Attempts on Specific Dates**

To investigate a suspicious event, the team needed to retrieve all login attempts that occurred on '2022-05-09' and the day before ('2022-05-08').

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  WHERE login\_date \= '2022-05-09' OR login\_date \= '2022-05-08';

* **Simulated Output (Excerpt):**  
  \+----------+----------+------------+----------+---------+---------+  
  | login\_id | username | login\_date | login\_time | country | success |  
  \+----------+----------+------------+----------+---------+---------+  
  | 201      | userA    | 2022-05-08 | 08:00:00 | USA     | 1       |  
  | 202      | userB    | 2022-05-08 | 08:15:00 | Canada  | 1       |  
  | ...      | ...      | ...        | ...      | ...     | ...     |  
  | 275      | userC    | 2022-05-09 | 17:45:00 | USA     | 1       |  
  \+----------+----------+------------+----------+---------+---------+  
  75 rows in set (0.025 sec)

* **Analysis:** This query accurately returned 75 login attempts made on the specified two days. The OR operator allowed for the inclusion of records matching either of the two date conditions, providing a comprehensive view of activity during the critical period.

## **3\. Retrieving Login Attempts Outside of Mexico**

To identify login attempts from unexpected geographical locations, the team needed to find all logins that did not originate in Mexico (considering both 'MEX' and 'MEXICO' entries).

* **SQL Query:**  
  SELECT \*  
  FROM log\_in\_attempts  
  WHERE NOT country LIKE 'MEX%';

* **Simulated Output (Excerpt):**  
  \+----------+----------+------------+----------+---------+---------+  
  | login\_id | username | login\_date | login\_time | country | success |  
  \+----------+----------+------------+----------+---------+---------+  
  | 101      | userD    | 2023-01-01 | 09:00:00 | USA     | 1       |  
  | 102      | userE    | 2023-01-01 | 09:30:00 | Canada  | 1       |  
  | ...      | ...      | ...        | ...      | ...     | ...     |  
  | 244      | userF    | 2023-01-10 | 14:00:00 | USA     | 1       |  
  \+----------+----------+------------+----------+---------+---------+  
  144 rows in set (0.040 sec)

* **Analysis:** This query successfully identified 144 login attempts made outside of Mexico. The combination of NOT and LIKE 'MEX%' effectively excluded all Mexican entries, allowing the team to focus on international logins for further scrutiny.

## **4\. Retrieving Employees in Marketing (East Building)**

For targeted machine updates, information was needed about employees in the 'Marketing' department who were located in offices in the 'East' building.

* **SQL Query:**  
  SELECT \*  
  FROM employees  
  WHERE department \= 'Marketing' AND office LIKE 'East%';

* **Simulated Output (Excerpt):**  
  \+-------------+----------+------------+-----------+-----------------+  
  | employee\_id | username | department | office    | phone\_extension |  
  \+-------------+----------+------------+-----------+-----------------+  
  | 1007        | elarson  | Marketing  | East-170  | 7001            |  
  | 1022        | snguyen  | Marketing  | East-320  | 7002            |  
  | ...         | ...      | ...        | ...       | ...             |  
  \+-------------+----------+------------+-----------+-----------------+

* **Analysis:** This query accurately retrieved records for employees meeting both criteria. The AND operator ensured that only employees in the 'Marketing' department *and* in the 'East' building were returned. The username of the first employee found was elarson.

## **5\. Retrieving Employees in Finance or Sales**

For a different computer update, information was needed about all employees in either the 'Finance' or the 'Sales' department.

* **SQL Query:**  
  SELECT \*  
  FROM employees  
  WHERE department \= 'Finance' OR department \= 'Sales';

* **Simulated Output (Excerpt):**  
  \+-------------+----------+------------+-----------+-----------------+  
  | employee\_id | username | department | office    | phone\_extension |  
  \+-------------+----------+------------+-----------+-----------------+  
  | 1001        | lrodriqu | Sales      | East-201  | 6001            |  
  | 1003        | jdoe     | Finance    | North-101 | 5001            |  
  | ...         | ...      | ...        | ...       | ...             |  
  \+-------------+----------+------------+-----------+-----------------+

* **Analysis:** This query successfully retrieved records for employees in either the 'Finance' or 'Sales' department. The OR operator allowed for the inclusion of records matching either departmental condition. The username of the first employee in the Sales department returned was lrodriqu.

## **6\. Retrieving All Employees Not in IT**

For a final update that had already been applied to IT department computers, information was needed about all employees *not* in the 'Information Technology' department.

* **SQL Query:**  
  SELECT \*  
  FROM employees  
  WHERE NOT department \= 'Information Technology';

* **Simulated Output (Excerpt):**  
  \+-------------+----------+------------+-----------+-----------------+  
  | employee\_id | username | department | office    | phone\_extension |  
  \+-------------+----------+------------+-----------+-----------------+  
  | 1001        | lrodriqu | Sales      | East-201  | 6001            |  
  | 1003        | jdoe     | Finance    | North-101 | 5001            |  
  | ...         | ...      | ...        | ...       | ...             |  
  \+-------------+----------+------------+-----------+-----------------+  
  161 rows in set (0.035 sec)

* **Analysis:** This query accurately identified 161 employees who are not in the 'Information Technology' department. The NOT operator effectively excluded the specified department, providing the target list for the remaining updates.

## **Conclusion**

This SQL analysis demonstrated the critical role of logical operators (AND, OR, NOT) in performing complex and precise data filtering for various security operations. By combining these operators with comparison and string matching capabilities, the security team can efficiently extract highly specific information from large datasets, enabling targeted investigations, policy enforcement, and effective asset management. This expertise in advanced SQL querying is invaluable for any cybersecurity analyst.