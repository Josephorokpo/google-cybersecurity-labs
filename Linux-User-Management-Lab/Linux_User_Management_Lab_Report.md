# **Linux User Management Lab Report**

## **Activity Overview**

This lab activity focused on using Linux commands to manage user access, covering essential concepts of authentication and authorization. It involved adding new users, assigning file ownership, modifying group memberships, and deleting users from the system.

## **Scenario Execution**

In this scenario, I managed the access for a new employee, researcher9, throughout their lifecycle within an organization. All commands executed required root (super user) privileges, thus prefixed with sudo. The lab started with the analyst user logged in, with /home/analyst as the current working directory.

### **Task 1: Add a new user**

A new employee, researcher9, joined the Research department. This task involved adding them to the system and assigning them to their primary group, research\_team.

* **Objective 1: Add a user called researcher9 to the system.**  
  * **Command:**  
    sudo useradd researcher9

  * **Output (implied):** No direct output on successful user creation.  
* **Objective 2: Add researcher9 to the research\_team group as their primary group.**  
  * **Command:**  
    sudo usermod \-g research\_team researcher9

  * **Output (implied):** No direct output on successful modification.  
  * **Alternative Command (combining useradd and primary group assignment):**  
    sudo useradd researcher9 \-g research\_team

  * **Verification (implied):** While not explicitly requested in the lab, one could verify group membership using id researcher9 or groups researcher9.

### **Task 2: Assign file ownership**

The new employee, researcher9, was assigned responsibility for project\_r. This task involved making them the owner of the project\_r.txt file, which was located in /home/researcher2/projects and initially owned by researcher2.

* **Objective: Make researcher9 the owner of /home/researcher2/projects/project\_r.txt.**  
  * **Command:**  
    sudo chown researcher9 /home/researcher2/projects/project\_r.txt

  * **Output (implied):** No direct output on successful ownership change.  
  * **Verification (implied):** One could verify the ownership change using ls \-l /home/researcher2/projects/project\_r.txt.

### **Task 3: Add the user to a secondary group**

A couple of months later, researcher9's role expanded to include work in the Sales department. This task involved adding them to a secondary group (sales\_team), while their primary group remained research\_team.

* **Objective: Add researcher9 to the sales\_team group as a secondary group.**  
  * **Command:**  
    sudo usermod \-a \-G sales\_team researcher9

  * **Output (implied):** No direct output on successful modification.  
  * **Note:** The \-a option (append) is crucial here to add the user to the new group without removing them from existing secondary groups. The \-G option specifies the secondary group(s). Options for Linux commands are case-sensitive.  
  * **Verification (implied):** One could verify group memberships using id researcher9 or groups researcher9.

### **Task 4: Delete a user**

A year later, researcher9 left the company. This task involved removing their account from the system and cleaning up any associated groups.

* **Objective 1: Delete researcher9 from the system.**  
  * **Command:**  
    sudo userdel researcher9

  * **Output:**  
    userdel: Group researcher9 not removed because it is not the primary group of user researcher9.

  * **Analysis:** This output is expected. When a user is created, a default group with the same name is often created as their primary group. If the user's primary group was later changed (as it was in Task 1 to research\_team), the userdel command by default won't remove the original, now empty, user-private group.  
* **Objective 2: Delete the researcher9 group that is no longer required.**  
  * **Command:**  
    sudo groupdel researcher9

  * **Output (implied):** No direct output on successful group deletion.  
  * **Analysis:** It is good practice to clean up any empty groups that remain after a user is deleted to maintain a tidy system.

## **Conclusion**

This lab provided practical experience in using fundamental Linux Bash shell commands to manage user access. I successfully demonstrated how to add new users, assign them to primary and secondary groups, change file ownership, and delete user accounts along with their associated groups. These are essential skills for any security analyst responsible for user management and access control in a Linux environment.