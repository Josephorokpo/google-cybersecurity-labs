# **Linux Package Management Lab Report**

## **Activity Overview**

This lab focused on gaining practical experience with the Advanced Package Tool (APT) and the sudo command within a Debian-based Linux Bash shell. The objective was to learn how to install, uninstall, and list applications, specifically using Suricata and tcpdump as examples of network security tools. The use of a virtual machine ensured a safe environment for practicing these essential Linux administration skills.

## **Scenario Execution**

As a security analyst, the task was to manage the installation of Suricata and tcpdump on a Linux system. The following steps were performed:

### **Task 1: Ensure that APT is installed**

* **Command Executed:**  
  apt

* **Output Observed:** The Bash shell displayed the basic usage information for apt, including its version (apt 1.8.2.3 (amd64)) and a description of its functionality.  
* **Verification:** This output confirmed that APT was correctly installed and operational, serving as the primary package manager for the Debian-based system.

### **Task 2: Install and uninstall the Suricata application**

* **Install Suricata:**  
  * **Command Executed:**  
    sudo apt install suricata

  * **Output Observed:** The terminal displayed a list of packages to be installed, including Suricata and its dependencies. When prompted to continue, the default 'Yes' was accepted by pressing ENTER. The installation process then proceeded, showing progress updates.  
  * **Verification:**  
    * **Command Executed:**  
      suricata

    * **Output Observed:** The terminal displayed Suricata's version (Suricata 4.1.2) and usage information, confirming successful installation.  
* **Uninstall Suricata:**  
  * **Command Executed:**  
    sudo apt remove suricata

  * **Output Observed:** The terminal listed the packages that would be removed. When prompted to continue, the default 'Yes' was accepted by pressing ENTER, and the uninstallation process completed.  
  * **Verification:**  
    * **Command Executed:**  
      suricata

    * **Output Observed:** The terminal displayed an error message: \-bash: /usr/bin/suricata: No such file or directory.  
    * **Verification:** This error message confirmed that the Suricata executable was no longer found in the system's PATH, indicating successful uninstallation.

### **Task 3: Install the tcpdump application**

* **Command Executed:**  
  sudo apt install tcpdump

* **Output Observed:** The terminal displayed the installation progress for tcpdump and its dependencies.  
* **Verification:** The command completed without errors, indicating a successful installation.

### **Task 4: List the installed applications**

* **Command Executed:**  
  apt list \--installed

* **Output Observed:** A long list of all installed applications was displayed.  
* **Verification:** I scrolled through the list and successfully located tcpdump/oldstable,now 4.9.3-1\~deb10u2 amd64 \[installed\], confirming its presence. Suricata was confirmed to be absent from this list, as expected from the previous uninstallation.

### **Task 5: Reinstall the Suricata application**

* **Reinstall Suricata:**  
  * **Command Executed:**  
    sudo apt install suricata

  * **Output Observed:** Similar to the initial installation, the terminal showed the packages being installed. The default 'Yes' was accepted when prompted.  
* **Verify Both Applications are Installed:**  
  * **Command Executed:**  
    apt list \--installed

  * **Output Observed:** The comprehensive list of installed applications was displayed again.  
  * **Verification:** Both suricata/oldstable,now 1:4.1.2-2+deb10u1 amd64 \[installed\] and tcpdump/oldstable,now 4.9.3-1\~deb10u2 amd64 \[installed\] were successfully found in the output, confirming that both required applications were installed.

## **Conclusion**

This lab provided practical, hands-on experience with fundamental Linux package management operations using APT and sudo. I successfully installed, uninstalled, and listed applications, demonstrating a core skill set for cybersecurity analysts who frequently work within Linux environments to deploy and manage security tools. This foundational knowledge is crucial for effective system administration and security operations.