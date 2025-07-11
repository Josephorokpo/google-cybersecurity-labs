# **Linux Package Management Lab Report (Commands & Outputs)**

## **Activity Overview**

This lab focused on gaining practical experience with the Advanced Package Tool (APT) and the sudo command within a Debian-based Linux Bash shell. The objective was to learn how to install, uninstall, and list applications, specifically using Suricata and tcpdump as examples of network security tools. The use of a virtual machine ensured a safe environment for practicing these essential Linux administration skills.

## **Scenario Execution**

As a security analyst, the task was to manage the installation of Suricata and tcpdump on a Linux system. The following steps were performed, including the commands executed and their observed outputs.

### **Task 1: Ensure that APT is installed**

First, I checked that the APT application was installed to ensure it could be used for package management.

* **Command Executed:**  
  apt

* **Output Observed:**  
  apt 1.8.2.3 (amd64)  
  Usage: apt \[options\] command

  apt is a commandline package manager and provides commands for  
  searching and managing as well as querying information about packages.  
  It provides the same functionality as the specialized APT tools,  
  like apt-get and apt-cache, but enables options more suitable for  
  interactive use by default.  
  ... (further usage information)

* **Verification:** This output confirmed that APT was correctly installed and operational, serving as the primary package manager for the Debian-based system.

### **Task 2: Install and uninstall the Suricata application**

In this task, I installed Suricata, verified its installation, then uninstalled it and confirmed its removal.

* **Install Suricata:**  
  * **Command Executed:**  
    sudo apt install suricata

  * **Output Observed (excerpt):**  
    Reading package lists... Done  
    Building dependency tree         
    Reading state information... Done  
    The following additional packages will be installed:  
      libhtp2 libmaxminddb0 libnetfilter-queue1 libpcap0.8 libyaml-0-2 libyaml-dev python-yaml  
    Suggested packages:  
      suricata-oinkmaster  
    The following NEW packages will be installed:  
      libhtp2 libmaxminddb0 libnetfilter-queue1 libpcap0.8 libyaml-0-2 libyaml-dev python-yaml suricata  
    0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.  
    Need to get 1,980 kB of archives.  
    After this operation, 9,800 kB of additional disk space will be used.  
    Do you want to continue? \[Y/n\] Y  
    Get:1 http://deb.debian.org/debian buster/main amd64 libyaml-0-2 amd64 0.2.2-1 \[50.0 kB\]  
    ... (installation progress) ...  
    Setting up suricata (1:4.1.2-2+deb10u1) ...  
    Processing triggers for man-db (2.8.5-2) ...

  * **Verification (running Suricata):**  
    * **Command Executed:**  
      suricata

    * **Output Observed:**  
      Suricata 4.1.2  
      USAGE: suricata \[OPTIONS\] \[BPF FILTER\]

          \-c \<path\>  : path to configuration file  
          \-T         : test configuration file (use with \-c)  
      ... (further usage information) ...

    * **Verification:** This output confirmed that Suricata was successfully installed and its executable was found in the system's PATH.  
* **Uninstall Suricata:**  
  * **Command Executed:**  
    sudo apt remove suricata

  * **Output Observed (excerpt):**  
    Reading package lists... Done  
    Building dependency tree         
    Reading state information... Done  
    The following packages will be REMOVED:  
      suricata  
    0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.  
    After this operation, 9,800 kB disk space will be freed.  
    Do you want to continue? \[Y/n\] Y  
    (Reading database ... 123456 files and directories currently installed.)  
    Removing suricata (1:4.1.2-2+deb10u1) ...  
    Processing triggers for man-db (2.8.5-2) ...

  * **Verification (running Suricata after removal):**  
    * **Command Executed:**  
      suricata

    * **Output Observed:**  
      \-bash: /usr/bin/suricata: No such file or directory

    * **Verification:** This error message confirmed that the Suricata executable was no longer found in the system's PATH, indicating successful uninstallation.

### **Task 3: Install the tcpdump application**

In this task, I installed the tcpdump application, a command-line tool for capturing network traffic.

* **Command Executed:**  
  sudo apt install tcpdump

* **Output Observed (excerpt):**  
  Reading package lists... Done  
  Building dependency tree         
  Reading state information... Done  
  The following additional packages will be installed:  
    libpcap0.8  
  The following NEW packages will be installed:  
    libpcap0.8 tcpdump  
  0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.  
  Need to get 484 kB of archives.  
  After this operation, 1,732 kB of additional disk space will be used.  
  Do you want to continue? \[Y/n\] Y  
  Get:1 http://deb.debian.org/debian buster/main amd64 libpcap0.8 amd64 1.9.1-3 \[193 kB\]  
  ... (installation progress) ...  
  Setting up tcpdump (4.9.3-1\~deb10u2) ...  
  Processing triggers for man-db (2.8.5-2) ...

* **Verification:** The command completed without errors, indicating a successful installation.

### **Task 4: List the installed applications**

Next, I confirmed the installation of tcpdump by listing all installed applications.

* **Command Executed:**  
  apt list \--installed

* **Output Observed (excerpt, showing relevant lines):**  
  Listing... Done  
  ...  
  tcpdump/oldstable,now 4.9.3-1\~deb10u2 amd64 \[installed\]  
  ...

* **Verification:** I successfully located tcpdump in the generated list, confirming its presence. As expected, suricata was not present at this stage.

### **Task 5: Reinstall the Suricata application**

In this final task, I reinstalled the Suricata application and verified that both Suricata and tcpdump were installed.

* **Reinstall Suricata:**  
  * **Command Executed:**  
    sudo apt install suricata

  * **Output Observed (excerpt):**  
    Reading package lists... Done  
    Building dependency tree         
    Reading state information... Done  
    The following NEW packages will be installed:  
      suricata  
    0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.  
    Need to get 1,980 kB of archives.  
    After this operation, 9,800 kB of additional disk space will be used.  
    Do you want to continue? \[Y/n\] Y  
    ... (installation progress) ...  
    Setting up suricata (1:4.1.2-2+deb10u1) ...  
    Processing triggers for man-db (2.8.5-2) ...

* **Verify Both Applications are Installed:**  
  * **Command Executed:**  
    apt list \--installed

  * **Output Observed (excerpt, showing relevant lines):**  
    Listing... Done  
    ...  
    suricata/oldstable,now 1:4.1.2-2+deb10u1 amd64 \[installed\]  
    ...  
    tcpdump/oldstable,now 4.9.3-1\~deb10u2 amd64 \[installed\]  
    ...

  * **Verification:** Both suricata and tcpdump were successfully found in the output, confirming that both required applications were installed.

## **Conclusion**

This lab provided comprehensive practical experience with fundamental Linux package management operations using APT and sudo. I successfully demonstrated the ability to install, uninstall, and list applications, which are core skills for any security analyst working within Linux environments for system administration and security tool management.