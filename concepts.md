# Concepts

> NOTE: These notes are very random and  These are some concept but are not in detail and explained enough , so it’s best to treat them as concepts to research on , so do your on deep dive into each of the concepts using Google, Youtube and AI
> 

> Created by Salman Al Qureshi
Linkedin: Salman Qureshi
> 
> 
> http://www.linkedin.com/in/salman-qureshi-4aa41a247
> 

## Linux Deep Dive

- linux is made by linus benedict tornvalds, first version was released in 1991 on the internet
- **Shell** in linux means a program that serves as a interface between the user and the computer OS . there are many linux shell types like bash, zsh, cshell, sh shell etc .
- linux file system is how linux stores files and folders and how it manages them

![Untitled](Concepts%202193e043159d819a8333d6485cba16d5/Untitled.png)

- **Interpreted languages** takes the code and then an interpreter program reads the source code line by line, translates it to a format the computer understands, and executes it immediately., This process happens each time the code is executed that’s why these code needs an interpreter to be executed . Because of the on-the-fly translation, interpreted code can be slower than compiled code.
- **Compiled languages**  in these languages the program is converted into machine code and then saved in a file as an executable, This conversion happens once and this process is called compiling, once this process is done, the code can be sent to others without any need for compiler
- **Scripting** involves writing scripts or small programs to automate tasks or manipulate existing systems. It is characterized by its focus on rapid development and ease of use. Scripting languages such as Python, Perl, and JavaScript are commonly used for tasks like system administration, web development, and automation. Scripts are typically executed line by line by an interpreter without the need for compilation, allowing for quick testing and modification. The scripting development process often emphasizes rapid prototyping and iterative development, enabling developers to solve specific problems efficiently. Overall, scripting provides a flexible and efficient approach to automating tasks and simplifying complex operations.
- **Programming** encompasses a broader range of activities, including designing, implementing, and maintaining software systems. Unlike scripting, programming involves a more structured approach to software development. Programming languages such as C, C++, Java, and C# offer extensive control over system resources and performance optimization. Programs are typically compiled into machine code or bytecode before execution, which can provide better performance but may require additional steps in the development process. The programming development process involves various stages, including requirements analysis, design, testing, debugging, and maintenance. While scripting focuses on smaller, specialized tasks, programming addresses a wider range of software development needs, from applications and games to operating systems and databases.

# **RHEL**:

- In linux almost commands are developed in C language & then converted in binary. In windows we call it exe & in linux we call it [binary.In](http://binary.in/) windows we call it restart & in linux we call it reboot. Windows have registry & in linux no registry but FS hierarchy. Windows have defrag & in linux no defrag because of the way how files are written. So anyways commands are atlast binary file which are kept in some path[location] from where we call them & run it as a command.
- **Inode** is a special data structure in a Unix-like filesystem that stores information about a file or a directory, but not its name or its actual data. Instead, it stores:
**Metadata**: Details like file size, permissions, owner, and timestamps.
**Data Pointers**: Locations of the actual data blocks on the disk.
every file has a unique inode number you can view with ls -i
- **Hard link and Soft link**:
hard links and soft links provide different ways to reference and manage files within a filesystem. Soft-link can cross and navigate through partitions but if the actual file(father file) gets deleted then the link will be of no use and will turn into an orphan link ( no father/actual file) , while hard-link cannot navigate through partitions but can still contain the data if the actual file(father file) gets deleted
- **Runlevels** are a concept used in Unix and Linux operating systems to define different states or modes of system operation. Each runlevel represents a specific system configuration and allows the system to be in different modes

In traditional System V (SysV) init systems, runlevels are represented by numbers, typically from 0 to 6. Each runlevel has a standard purpose:
**Runlevel 0**: Halt (shutdown the system)
**Runlevel 1**: Single-user mode (for administrative tasks)
**Runlevel 2**: Multi-user mode without networking
**Runlevel 3**: Multi-user mode with networking (text mode, no graphical interface)
**Runlevel 4**: Undefined (customizable for user-defined purposes)
**Runlevel 5**: Multi-user mode with networking and graphical interface (GUI)
**Runlevel 6**: Reboot (restart the system)

You can change the runlevel using the init or telinit command. For example, to switch to runlevel 3, you can use:
sudo init 3
To see the current and previous runlevels, you can use the `runlevel` command
**Note:** 
Modern Linux distributions have largely transitioned to using `systemd` instead of the traditional SysV init system. In `systemd`, runlevels are replaced by "targets," which provide a more flexible way of defining system states.
if we do cat /etc/inittab it also shows us this 
systemd uses 'targets' instead of runlevels. By default, there are two main targets:
multi-user.target: analogous to runlevel 3
graphical.target: analogous to runlevel 5
To view current default target, run:
systemctl get-default
To set a default target, run:
systemctl set-default TARGET.target
- In CentOS 7, the concept of runlevels is managed by systemd targets. You can switch between targets using the `systemctl isolate` command and set the default target with `systemctl set-default`. This system allows you to manage the state of your system efficiently, whether you're aiming for a graphical interface or a multi-user command-line environment.
**Systemd Targets**: Modern replacement from runlevels in CentOS 7.
**Common Targets**:
`rescue.target` (Single user mode)
`multi-user.target` (Non-graphical, multi-user)
`graphical.target` (Graphical interface)
`reboot.target` (Reboot the system)
`poweroff.target` (Shut down the system)
**Switching Targets**: Use `sudo systemctl isolate TARGET`.
**Setting Default Target**: Use `sudo systemctl set-default TARGET`.
- **Splash Screen**: An image or animation displayed during the boot process to provide user feedback and improve aesthetics.
**Systems**: Plymouth is the most common system used in modern Linux distributions for managing splash screens.
# we can also interrupt and use a console here to go to a different runlevel/systemd, default will still be the same as it has to be changed from the configuration files
- **A Filesystem** is a method used by an operating system to organize, store, and manage files and directories on a storage device like a hard drive or SSD. It keeps track of where data is located, how it is accessed, and includes information about file names, sizes, and permissions.
A filesystem (FS) is typically created for each partition or volume on a disk, rather than for each individual piece of data or for the entire disk as a single entity.
When a filesystem is created, it is done on a partition or a volume. This process involves formatting the partition with a filesystem type (e.g., ext4, NTFS, FAT32).
If you have multiple partitions, you can create a separate filesystem on each partition. Each partition will independently manage its data using its filesystem.
# Use tools like `fdisk`, `parted`, or graphical disk management utilities to create partitions on your disk.
Use commands like `mkfs.ext4` to create an ext4 filesystem on a specific partition, This process sets up the necessary data structures (like superblocks, inodes, and data blocks) on each partition.
Filesystems are created on partitions or volumes, but to use them, they need to be integrated into the directory structure.
Mounting connects the filesystem to a directory (the mount point) so that users and applications can access files and directories within that filesystem.
**Mounting**: The process of attaching a filesystem to a specific directory (mount point) in the Linux directory tree.
**Purpose**: To make filesystems accessible and integrate different storage devices into the directory structure.
Example:
To access a filesystem, you first need to create a directory that will serve as the mount point. For example, you can create a directory called `/mnt/external` by using the command `sudo mkdir /mnt/external`. This directory will be where you can access the contents of the filesystem once it is mounted. Next, you use the `mount` command to attach the filesystem to the mount point. For instance, if your device identifier is `/dev/sdb1`, you can mount the filesystem with the command `sudo mount /dev/sdb1 /mnt/external`. After executing this command, the files on the device will be accessible through the `/mnt/external` directory.
# But this is not permanent and will be delete after a reboot , to have a permanent follow the following instructions 
To make the mount permanent, you need root privileges to edit the **`/etc/fstab` which is a boot process file**  file. You can use any text editor, such as `nano` or `vim`, by running the command `sudo nano /etc/fstab`. Add a line at the end of the file with the details of the filesystem in the format: 
<`<device> <mount_point> <filesystem_type> <options> <dump> <pass>`>. 
For example, to make the `/dev/sdb1` mount to `/mnt/external` permanent, you might add: <`/dev/sdb1 /mnt/external ext4 defaults 0 2`>.
 Adjust the `filesystem_type` (e.g., `ext4`, `ntfs`) and options as needed. 
/dev/sdb1: The device identifier.
/mnt/external: The mount point.
ext4: The filesystem type.
defaults: The mount options (default options).
0: The dump value (not backed up by dump)
2: The pass value (checked by fsck after the root filesystem; 0 to skip check).
- A partition table is a data structure on a storage device such as a hard disk or solid-state drive that describes the layout of the disk's partitions. It provides information about the starting and ending points of each partition, the type of each partition, and other relevant metadata. This information is crucial for the operating system to correctly manage and access the different partitions on the disk.
most common types are:
**Master Boot Record (MBR)
GUID Partition Table (GPT)
Apple Partition Map (APM)**
- network can have multiple gateways but the default gateway can only be one

- IP aliasing is a technique used to assign multiple IP addresses to a single network interface. This allows a single physical interface to be configured with multiple logical IP addresses, enabling it to handle traffic for multiple IP addresses. IP aliasing is commonly used in scenarios where multiple services need to run on a single machine with different IP addresses or for network management purposes.
IP aliasing is typically configured by creating additional network interface configurations, often named using a colon (`:`) to denote aliases, such as `eth0:0`, `eth0:1`, etc.Each alias is treated as a separate logical interface with its own IP address, even though they share the same physical hardware.
- All ports and services on them are mentioned in /etc/services
- There are 65535 total ports in which 1023 ports are privileged ports and the rest are non-privileged poerts
- **RPM (Red Hat Package Manager)
RPM** is a powerful package management system used by Red Hat-based distributions (such as CentOS, Fedora, and RHEL) to manage software packages. It allows users to install, update, uninstall, verify, and query software packages.
Key Characteristics:
**Binary Format**: RPM packages are typically distributed in binary format with a `.rpm` extension.
**Dependency Management**: RPM handles software dependencies to ensure that all required libraries and packages are installed.
**Database of Installed Packages**: RPM maintains a database of installed packages to track and manage them efficiently.

**DPKG (Debian Package Manager)**
**DPKG** is the package management system used by Debian-based distributions (such as Ubuntu and Debian itself) to manage software packages. It works with `.deb` packages and provides low-level functions for installing, updating, and removing packages.
Key Characteristics:
**Binary Format**: DPKG packages are distributed in binary format with a `.deb` extension.
**Basic Package Management**: DPKG focuses on basic package management functions, and higher-level tools like `apt` or `synaptic` are often used for dependency management
**Database of Installed Packages**: DPKG maintains a database of installed packages to track and manage them efficiently.
- **swap** refers to a space on a hard drive that is used as virtual memory when the physical RAM (Random Access Memory) is fully utilized. When the system runs out of physical memory, it can temporarily transfer data from RAM to the swap space on the disk. This process is called swapping.
it uses VFS file system
- QN:
One of the server has high utilization what will you do ?
OR
one of the process is eating memory 
OR
one of the process is eating processor 
What will you do ??
ANS:
i will use some performance monitoring tools  and see how much memory and processor is being used and then see what application is using the most , then contact/engage with that app team
And if the load wasen’t because of an app then i will check the HDD and network traffic using tools like fdisk or iostat to check storage and tcpdump or wireshark for network traffic 
OR sar which can be used for monitoring many thing 
Another thing to check is the buffer and cache is these are high then performance can decrease 
OR There can be a hardware fault
- **Buffers** are temporary storage areas in RAM used by the kernel to hold data that is in the process of being moved from one place to another. Specifically, they are used for data that is in transit, such as data being written to or read from disk.
**Purpose**: The primary purpose of buffers is to optimize disk I/O operations. By using buffers, the system can accumulate multiple disk I/O requests and process them in one go, which reduces the overhead of multiple, smaller I/O operations.
- **Cache** refers to memory used by the kernel to store data that has been read from disk and might be read again soon. The idea is to keep frequently accessed data in RAM so that the system can access it quickly without having to read from disk each time.
**Types of Cache**:
**Page Cache**: Stores actual file data that has been read from disk.
**Dentries and Inodes Cache**: Stores metadata about files and directories.
**Purpose**: The primary purpose of the cache is to speed up data access and improve overall system performance by reducing the need for repeated disk access.
- Logical Volume Manager (LVM)
LVM allows for flexible disk management, enabling the resizing of logical volumes as needed. 
Tip: Whenever you  need to add/make a disk or mount point first make a volume group and then add to that cuz with that you can always add more disk/storage to that vg and then create lv(logical volumes ) , and you can directly add a disk or make patitions from the disk and then add that partitions its upto you, how to do that ? the process is in linux commands notes
- **Patching** is the process of updating software to fix vulnerabilities, improve performance, or add features. It is essential for security, stability, and efficiency. The patching process involves identification, assessment, deployment, and verification to ensure systems remain protected and functional. Regular patching is a critical component of effective system and software management.
- Permission Bits
File permissions in Unix-like systems use a 3-bit binary number to represent each set of permissions (owner, group, others). Each bit corresponds to a specific permission:
**Read (r)**: Represented by the highest bit, which has a value of 4 (2^2 = 4)
**Write (w)**: Represented by the middle bit, which has a value of 2 (2^1 = 2).
**Execute (x)**: Represented by the lowest bit, which has a value of 1 (2^0 = 1).
- Special permissions: # IMP TOPIC
**SUID (Set User )**: if this is set on a file then whoever runs this file will be executing it with owners permissions , so if the owner’s permission was rwx then the user will also have these permissions when executing the file 
**Example**: The `passwd` command lets users change their passwords. Normally, changing a password requires modifying system files, which need root permissions. By setting the SUID bit on `passwd`, any user can run it with root privileges, but only for the scope of changing passwords.
**SGID (Set Group ID):** if this is set on a file then whoever runs this file will be executing it with Group permissions , so if the group’s permission where rwx then the user will also have these permissions when executing the file 
**Sticky Bit:**
**Purpose**: Prevents users from deleting or renaming files in a directory unless they own the file or directory.
**Real-World Example**: The `/tmp` directory is writable by all users, but you don't want users to delete each other's files.
**Scenario**: You have a directory `/public` where everyone can write files, but only file owners can delete their files.

**sudoers:** Allows specific users or groups to perform administrative tasks without giving them full root access. This minimizes security risks associated with providing full root access to multiple users.
The `sudoers` file is a configuration file for the `sudo` command on Unix-like operating systems.
 The file is located at `/etc/sudoers`.

umask: This is the defult permission given to a file/directory made
- The admin in linux are the users how has the uid of 0 and root user has uid 0 thats why he is the super user
- Kernel:
its the Engine or brain of the OS , it’s stored in /boot and is around 4,6 mb 
it uses drivers which are stored in /lib/modules/<kernel-version>/kernel/  and are called kernel drivers , these drivers use .ko extentions which stands for kernel object 

Peripheral Component Interconnect (PCI) is **a local computer bus for attaching hardware devices in a computer** and is part of the PCI Local Bus standard
- Types of kernel 
**Monolithic Kernel**: Combines all services and drivers into a single large block of code running in a single address space. It offers better performance but at the cost of potential stability and maintenance challenges.
**Microkernel**: Strips the kernel down to its most fundamental parts, with other services running in user space. This design improves stability and security but may suffer from performance overhead due to more complex communication.

Kernel tuning involves adjusting various parameters and settings of the kernel to optimize the performance, stability, and behavior of a Linux system. This process can help ensure that the system operates efficiently under specific workloads and conditions.
- AWS Services
    
    ![aws services.png](Cloud%20&%20SysOps%202193e043159d819897a1ff2b1ecadcd3/aws_services.png)
    
    ![Untitled](Cloud%20&%20SysOps%202193e043159d819897a1ff2b1ecadcd3/2024-07-01_20_18_47-(623)_Introduction_to_AWS_Services_-_YouTube.png)
    

> [https://youtu.be/Z3SYDTMP3ME?si=kM4GyxCuko0HSzaF](https://youtu.be/Z3SYDTMP3ME?si=kM4GyxCuko0HSzaF)
Youtube Video For Explanation.
> 
- Global Infrastructure (GI) is the overall picture of how many Regions and AZs AWS has deployed worldwide.
- Regions are like geographically distinct "zones" with complete AWS services.
- Availability Zones (AZs) are like individual data centers within a Region, offering high availability.
- **Infrastructure as a Service (IaaS):** This is the most basic layer. With IaaS, you rent virtual servers, storage, networking, and other fundamental computing resources. You have complete control over these resources, just like managing your own data center, but with the benefit of scalability and pay-as-you-go pricing offered by AWS.
- **Platform as a Service (PaaS):** PaaS provides a platform for developing, deploying, and managing applications. It eliminates the need to manage the underlying infrastructure (servers, storage, networking) as AWS takes care of that. You focus on building and deploying your applications on the platform.
- **Software as a Service (SaaS):** This offers ready-made applications delivered over the internet. You don't need to manage infrastructure or the platform; you simply access and use the software application for your specific needs. Popular examples of SaaS applications include Gmail, Dropbox, and Salesforce.
- EC2 instances come in various configurations, categorized into families based on their core functionalities. These families help you choose the instance type that best suits your workload's needs.
**Compute Optimized:** These instances are powerful in terms of CPU processing power, ideal for compute-intensive workloads like scientific simulations or video editing.
**Memory Optimized:** These instances offer large amounts of memory, making them suitable for applications requiring in-memory databases or large datasets.
**Storage Optimized:** These instances come with significant storage capacity, perfect for storing large amounts of data or running databases.
**General Purpose:** These instances offer a balanced mix of CPU, memory, and storage, suitable for a wide range of applications that don't have specific resource demands.
- AWS offers a variety of storage solutions to cater to different data storage needs. Here's a breakdown of the main storage types:
**Block Storage: Amazon Elastic Block Store (EBS)
Concept:** EBS provides persistent block storage volumes that behave like traditional hard disk drives (HDDs) or solid-state drives (SSDs). You can attach these volumes to your EC2 instances and use them to store data that persists even after instance termination.

**Object Storage: Amazon Simple Storage Service (S3)
Concept:** S3 is a highly scalable object storage service designed for storing and retrieving any amount of data, from a few kilobytes to petabytes. Data is stored as objects with unique identifiers, making it efficient for unstructured data like backups, archives, media files, and static website content.

**File Storage:
Amazon Elastic File System (EFS):** Provides a scalable, managed file system service for sharing data between EC2 instances in a single Availability Zone. It allows you to mount file systems to multiple instances simultaneously for collaborative editing and application access.
- Simple Monthly Calculator:
This is a calculator where we can check what services will cost, just google aws pricing calculator
- Amazon Inspector: Your Automated Security Guard
**Amazon Inspector** is a cloud-based security assessment service that helps you automatically assess the security of your applications deployed on AWS. It acts like an automated security auditor, continuously scanning your workloads for vulnerabilities and deviations from security best practices.
**Automated Vulnerability Scanning**
    
    **Network Exposure Assessment**
    
    **Security Best Practice Checks**
    
    **Continuous Security Monitoring**
    
    **Detailed Findings and Recommendations**
    

- NFS Network file sharing  service, port 2049, UDP protocol, standard is Linux to Linux, doesnt ask for username password # Add the Folder you want to share in /etc/exports
- Samba file sharing  service uses 137/139/335 port, tcp protocol, linux to lix OR linux to windows,  requires username & password
- **SELinux (Security-Enhanced Linux)** is a security module integrated into the Linux kernel that provides a mechanism for supporting access control security policies. It was originally developed by the NSA and is now a standard part of many Linux distributions, especially RHEL/CentOS and Fedora.
- **`named`** (pronounced as "name-dee") is the **BIND (Berkeley Internet Name Domain) DNS server** daemon. It stands for "name daemon" and is a crucial component of the BIND package, which is the most widely used DNS server software on the Internet. **`named`** provides DNS resolution services, translating domain names into IP addresses (and vice versa). 
The main configuration file for `named is /etc/named.conf`
- **`httpd`** is the executable name for the Apache HTTP Server daemon, which is one of the most popular and widely used web server software applications. It is part of the Apache HTTP Server Project and provides a robust, full-featured web server for serving web pages and other content over HTTP and HTTPS protocols.
IMP Files:
**`/etc/httpd/conf/httpd.conf`: T**he main configuration file for the Apache HTTP Server.
**`/etc/httpd/conf.d/`:**  Directory containing additional configuration files that are included in the main configuration.
**`/var/www/html/`:** Default document root directory where web content is stored.
- **Virtual Hosts** (vhosts) in Apache HTTP Server allow you to host multiple websites on a single server. This is achieved by using different configurations for each site, such as different domain names or IP addresses. Virtual hosts can be configured to serve different content based on the requested URL, making it possible to host multiple websites on a single server instance.
- Understanding Rolling Releases and `lsb_release`
    
    ### Rolling Releases
    
    In the world of Linux distributions, there are two primary release models:
    
    1. **Fixed Release Model:** This is the traditional model where a distribution releases a new version at specific intervals (e.g., Ubuntu every two years). Users upgrade to the new version when it's available.
    2. **Rolling Release Model:** In this model, the distribution is constantly updated with the latest software packages. There's no fixed release schedule, and users are always running the most recent stable versions.
    
    ### `lsb_release` Command
    
    The `lsb_release` command provides information about the Linux Standard Base (LSB) and the distribution you're using.
    
    **Commonly used options:**
    
    - **`lsb_release -a`:** Displays all available information.
    - **`lsb_release -d`:** Displays the distribution description.
    - **`lsb_release -r`:** Displays the release number.
    - **`lsb_release -c`:** Displays the codename (if available).
    
    **Example:**
    
    Bash
    
    `lsb_release -a`
    
    This command might output something like:
    
    `Distributor ID: Ubuntu
    Description:    Ubuntu 22.04.2 LTS (Jammy Jellyfish)
    Release:        22.04
    Codename:       jammy`
    
    In this example, Ubuntu follows a fixed release model with the codename "jammy" for the 22.04 LTS release.
    
    **However, for a rolling release distribution like Arch Linux, the output would be different:**
    
    Bash
    
    `Distributor ID: Arch
    Description:    Arch Linux
    Release:        rolling
    Codename:       n/a`
    
    Here, the `Release` field shows "rolling," indicating a continuous update model
    

### ESXI

VMware ESXi is

**a hypervisor software that allows users to create virtual machines (VMs) on physical servers.** It's a type-1 hypervisor, which means it's installed directly on the hardware and doesn't require an operating system (OS). ESXi is a key component of VMware's infrastructure software suite.

**Here are some features of ESXi:**

- **Bare-metal:** ESXi installs directly on the physical server, giving users direct access to the hardware's resources.
- **OS-independent:** ESXi is based on the VMkernel operating system and integrates OS components within itself.
- **Efficient resource management:** ESXi can efficiently divide hardware resources between VMs, allowing users to use the full capacity of their hardware.
- **Configuration:** ESXi allows users to configure the amount of CPU, memory, hard disk usage, and storage units for their environment.

ESXi was previously known as ESX, which was an abbreviation for Elastic Sky X. The name was changed to ESXi after version 4.1, released in 2010, with the "i" standing for "integrated".

### **Difference Between Metrics and Logs**

**1. Metrics**

- **Definition**: Metrics are numerical values that represent the state or performance of a resource at a specific point in time.
- **Characteristics**:
    - **Lightweight**: Metrics are optimized for near real-time monitoring.
    - **Time-series data**: Collected at regular intervals (e.g., CPU usage every minute).
    - **Predefined**: Generally collected by the system or service (e.g., disk IOPS, memory usage).
    - **Low storage**: Requires minimal storage space compared to logs.
- **Use Cases**:
    - Monitoring trends and system health (e.g., a spike in CPU usage).
    - Triggering alerts for real-time thresholds (e.g., alert if CPU > 80%).
- **Example**:
    - CPU utilization: `70%`
    - Number of active connections: `100`

---

**2. Logs**

- **Definition**: Logs are detailed records of events, actions, or errors captured by the system or application over time.
- **Characteristics**:
    - **Textual or Structured**: May include extensive details about a specific event.
    - **Event-focused**: Represents individual occurrences (e.g., login attempts, errors).
    - **High storage**: Can be voluminous depending on logging verbosity.
- **Use Cases**:
    - Debugging issues (e.g., why an application crashed).
    - Conducting audits (e.g., tracking user logins).
    - Security analysis (e.g., reviewing suspicious login attempts).
- **Example**:
    - `2024-12-14 14:05:30 ERROR: Application crashed due to timeout.`
    - `2024-12-14 14:06:00 INFO: User logged in from IP 192.168.1.1`

---

### **Key Differences**

| **Aspect** | **Metrics** | **Logs** |
| --- | --- | --- |
| **Data Type** | Numerical, time-series | Textual, event-based |
| **Frequency** | Continuous, periodic intervals | Generated when events occur |
| **Purpose** | Monitor performance and trends | Diagnose issues and analyze events |
| **Storage Size** | Lightweight | High storage requirements |
| **Real-Time** | Yes, near real-time monitoring | No, typically used for analysis |
| **Examples** | CPU usage, Memory utilization | Error logs, Access logs |
| **Visualization** | Graphs, Charts | Searchable text, Query results |

---

### **Summary**

- **Metrics** are for **quantitative performance monitoring** (e.g., "How much CPU is being used?").
- **Logs** are for **qualitative event details** (e.g., "Why did the application fail?").

# **CISSP:**

- In security, the **Common Body of Knowledge (CBK)** is a comprehensive framework of all the relevant subjects a security professional should be familiar with, including skills, techniques and best practices. The CBK is organized by domain and is annually gathered and updated by (ISC)2 ([International Information Systems Security Certification Consortium](https://www.techtarget.com/searchsecurity/definition/ISC2-International-Information-Systems-Security-Certification-Consortium)) to reflect the most relevant topics within the industry.
**CISSP CBK domains:**
The eight CISSP domains are the following:
1. **Security and Risk Management.** This domain deals with risk management concepts, threat modeling, the security model, security governance principles, [business continuity requirements](https://www.techtarget.com/searchdisasterrecovery/tip/Follow-these-standards-for-business-continuity-and-resilience), and policies and procedures.
2. **Asset Security.** This domain contains topics that involve data management and standards, longevity and use, how to ensure appropriate retention and how [data security controls](https://www.techtarget.com/searchsecurity/feature/Types-of-cybersecurity-controls-and-how-to-place-them) are determined.
3. **Security Engineering.** This domain tests a candidate on security engineering processes, models and design principles, including [database security](https://www.techtarget.com/searchsecurity/tip/4-enterprise-database-security-best-practices), cryptography systems, clouds and vulnerabilities.
4. **Communications and Network Security.** This domain includes network security and the creation of secure communication channels, such as [secure network architecture design](https://www.techtarget.com/searchnetworking/tip/Network-security-design-best-practices-and-principles-Keep-it-simple) and components including access control, transmission media and communication hardware.
5. **Identity and Access Management.** This domain focuses on system access, authorization, identification and authentication, including access control and [multifactor authentication](https://www.techtarget.com/searchsecurity/definition/multifactor-authentication-MFA).
6. **Security Assessment and Testing.** This domain covers the tools needed to find vulnerabilities, bugs and errors in code and system security, as well as vulnerability assessment, [penetration testing](https://www.techtarget.com/searchsecurity/tip/Pen-testing-guide-Types-steps-methodologies-and-frameworks) and disaster recovery.
7. **Security Operations.** This domain deals with digital forensic and investigations, detection tools, [firewalls](https://www.techtarget.com/searchsecurity/definition/firewall) and sandboxing, as well as incident management.
8. **Software Development Security.** This domain contains information on how to [build and integrate security into the software development lifecycle](https://www.techtarget.com/searchsecurity/tip/Top-4-best-practices-to-secure-the-SDLC).
- Governance = How an organization is managed.
- Merger = its when two companies combine into one
- Acquisition = its when one company buys another small company or any company
- Divestitures refer to the process by which a company sells, liquidates, or otherwise disposes of one of its business units, subsidiaries, or assets
- Due diligence is the process of conducting thorough investigations and evaluations about a particular thing—such as a business, investment, or partnership—before making a decision.
- **Compliance**: Adhering to Rules and Standards
**Compliance** means conforming to a set of rules, regulations, or standards. It's about acting in accordance with the law, industry best practices, or internal policies.
- Compliance validation refers to the process of assessing whether an individual, organization, system, or process complies with a specific set of rules, regulations, or standards. It is an essential component of ensuring security and adherence to industry best practices. Let's analyze each statement:
- BCP A business continuity plan is a document that explains the actions you should take before, during and after unexpected events and situations
- **A Disaster Recovery Plan (DRP) is a detailed strategy designed to help an organization recover and resume critical business functions in the event of a catastrophic disaster.** This could include natural disasters, power outages, cyberattacks, or any event that significantly disrupts normal operations.
- **Identity and Access Management (IAM)** is a framework of policies and technologies used to ensure that the right people have the appropriate access to technology resources. It's like a digital gatekeeper that controls who can enter a building and what rooms they can access.
    
    **Key components of IAM:**
    
    **Identification:** Determining who a user is (e.g., username, employee ID).
    
    **Authentication:** Verifying the user's identity (e.g., password, biometrics).
    
    **Authorization:** Granting specific permissions based on the user's role or job function.
    
    **Provisioning:** Creating and managing user accounts and access rights.
    
    **Governance:** Establishing policies and controls for identity and access management.
    
- An **Asset**, in a business context, refers to anything valuable that an organization owns or uses to achieve its goals. This can include both tangible and intangible assets.

**Tangible assets** are physical things you can see and touch, such as:
**Property:** Buildings, land, equipment (machinery, computers, vehicles)
**Inventory:** Raw materials, work-in-progress goods, finished products

**Intangible assets** are non-physical but still hold value for the organization, such as:
**Intellectual property:** Patents, copyrights, trademarks
**Brand reputation:** Brand recognition and customer loyalty
**Data:** Customer information, market research, financial records
**Human capital:** Skills, knowledge, and experience of employees
**Security management** is the identification of an organization's assets i.e. including people, buildings, machines, systems and information assets, followed by the development, documentation, and implementation of policies and procedures for protecting assets.
- **Asset lifecycle management** is the process of planning, acquiring, operating, maintaining, and disposing of an asset throughout its useful life. It's a systematic approach to ensure assets deliver the most value possible to the organization.
- An audit is a systematic examination of an organization's financial records, processes, and controls to ensure accuracy, compliance, and integrity of financial statements and reports. The main purpose of an audit is to provide an independent assessment of an organization's financial health and to give stakeholders confidence in the reliability of the financial information presented.
- **Internal audits:** Independent evaluations conducted within an organization to assess efficiency, effectiveness, and risk management of its operations. They help identify areas for improvement and ensure alignment with organizational goals.
- **External audits:** Independent assessments conducted by external auditors to provide an opinion on the fairness and accuracy of an organization's financial statements. They enhance credibility for investors and stakeholders.
- **Operational audits:** Deep dives into an organization's business processes to evaluate efficiency, effectiveness, and controls. They aim to optimize performance and identify opportunities for improvement.
- Audit evidence is the information collected by an auditor during an audit to support their **opinion on the fairness and accuracy** of a company's financial statements.
- An information systems audit is conducted to evaluate the effectiveness, efficiency, and security of an organization's information systems and technology infrastructure. The main objectives of an information systems audit include assessing the reliability and integrity of data, ensuring compliance with legal and regulatory requirements, identifying vulnerabilities and risks, and evaluating the adequacy of controls
- An audit trail is a record of events and activities that provides evidence and documentation of transactions and changes within a system. An effective audit trail should possess certain characteristics to ensure its reliability and usefulness, including completeness, accuracy, and the ability to trace and reconstruct transactions.
- **RPO** stands for Recovery Point Objective. It refers to the maximum amount of acceptable data loss after a disaster. In simpler terms, it's the point in time to which an organization aims to recover its data after a disaster.
**RTO** stands for Recovery Time Objective. This refers to the targeted duration of time it takes to resume critical business operations after a disaster.
**MTD** stands for Maximum Tolerable Downtime. This refers to the longest acceptable period a business can function without critical applications or data.

The bottom portion of the slide depicts a timeline that illustrates these concepts. It shows how data backups are taken at regular intervals (RPO). Then, in the event of a disaster (represented by a lightning bolt symbol), the organization aims to recover its systems and data within the RTO timeframe. This allows them to resume normal business operations as quickly as possible, minimizing the impact of the downtime (which should not exceed the MTD).
    
    ![Untitled](Concepts%202193e043159d819a8333d6485cba16d5/Untitled%201.png)
    
- Residual risk = Risk remaining after risk treatment 
**Residual risk:** The risk that remains after implementing controls. It highlights the effectiveness of the implemented controls in mitigating inherent risk.
- **Inherent risk:** The baseline level of risk associated with an activity before considering any controls. It's the natural risk due to the nature of the activity itself.
- **Personally identifiable information (PII):** PII, as it is referred to in the industry, is any data about a  human being that could be used to identify that person

- Standards and Frameworks Selection:
• Payment Card Industry Data Security Standard (PCI DSS)
• International Organization for Standardization (ISO)
• General Data Protection Regulation (GDPR)
• National Institute of Standards and Technology (NIST)
• European Network and Information Security Agency (ENISA)
• International Telecommunications Union (ITU)

- Discretionary Access Control (DAC):
Concept: DAC allows the owner of a resource (data, file, system) to decide who can access it and what level of access they have (read, write, execute). Think of it as the owner "granting the keys" to specific users.
Pros: Simple to implement and manage, especially for small groups or personal data.
Cons: Not very scalable for large organizations with many users and resources. Security relies heavily on responsible ownership, which can be a risk.
- Mandatory Access Control (MAC):
Concept: In MAC, access is centrally controlled by a security policy enforced by the system. The system labels both subjects (users) and objects (data) with security classifications (e.g., Top Secret, Confidential). Access is only granted if a user's security level is equal to or higher than the classification of the object they want to access. Think of it as a hierarchical system with strict clearance levels.
Pros: Provides strong security for highly sensitive data as access is predefined and not user-controlled.
Cons: Less flexible than DAC, can be complex to manage in dynamic environments, and might not be suitable for all types of data.
- Role-Based Access Control (RBAC):
Concept: RBAC associates users with predefined roles (e.g., administrator, editor, viewer). Each role has specific permissions assigned to it. Users are granted access based on their assigned roles. This simplifies administration as access changes are typically made to the role rather than individual users. Think of it as assigning pre-defined "toolkits" of permissions based on job functions.
Pros: More scalable and manageable than DAC for large organizations. Simplifies administration by controlling access through roles.
Cons: Requires careful design and definition of roles and permissions to ensure appropriate access levels.
- Attribute-Based Access Control (ABAC):
Concept: ABAC is a more dynamic approach that considers various attributes beyond just user roles and object classifications. Access decisions are based on a combination of factors, such as user attributes (department, location, security clearance), object attributes (sensitivity, project), environment attributes (time of day, network location). Think of it as a multi-layered access control system with a more granular approach.
Pros: Provides the most flexible and fine-grained access control decisions. Ideal for complex environments with diverse access requirements.
Cons: More complex to implement and manage than other models. Requires a robust system for attribute definition and evaluation.
- **Passive Attack**
**Definition**: Passive attacks involve monitoring or eavesdropping on communications or data without altering the information or the communication flow.
**Objective**: The main goal of passive attacks is to gain unauthorized access to information without detection.

**Active Attack**
**Definition**: Active attacks involve interacting with or modifying the communication or data in a system.
**Objective**: The main goal of active attacks is to alter, disrupt, or destroy data and systems, often with immediate and noticeable effects.

![Untitled](Concepts%202193e043159d819a8333d6485cba16d5/Untitled%202.png)

![image.png](Concepts%202193e043159d819a8333d6485cba16d5/image.png)

- An **attack surface**, in cybersecurity, refers to the sum of all possible entry points that a malicious actor (hacker) could exploit to gain unauthorized access to a computer system, network, or data. It's essentially the total area that's vulnerable to attack.
- In computer security, a **baseline** refers to a set of minimum security controls or configurations that are established for an information system. It's essentially the foundation for a secure system, defining the essential security measures that need to be in place.
- **Standards** are essentially documented agreements that define how things should be done. They establish a common ground for various stakeholders, including manufacturers, developers, and users. These standards can be technical specifications, best practices, or even guidelines for behavior.
- **Repudiation:**
Refers to the act of denying involvement in a transaction or communication.
In simpler terms, it's the ability of someone to claim they weren't responsible for something, even if they were.
This can be a problem in digital transactions where there's no physical proof of someone's involvement.
**Example of Repudiation:**
Alice sends a message to Bob saying she agrees to purchase a product. Later, Alice claims she never sent the message and denies the agreement.
- **Non-repudiation:**
Stands for the opposite concept. It ensures that a party involved in a transaction cannot deny their participation afterward.
In the digital world, it provides a mechanism to prove someone did something (e.g., sent a message, signed a document).
**Example of Non-repudiation:**
Bob uses a digital signature to approve a financial transaction. This signature acts as undeniable proof that Bob authorized the transaction.
- The policy and procedures stand on  three pillars ( PPT )
1. People
2. Processes
3. Technology
- as a code means automated 
so security as a code would mean automating the process of developing and implementing security measure in the organization 
OR
**"As Code"** refers to the practice of using code to automate tasks and processes. For example, **Security as Code** means using code to automate the development and implementation of security measures within an organization. This approach ensures consistency, repeatability, and efficiency by allowing security policies and controls to be defined, managed, and enforced through automated scripts and tools.
- **infrastructure as Code (IaC)** means treating your IT infrastructure (servers, networks, storage) like software. Instead of manually configuring these components, you use code to define and manage them.

- Difference between information and cyber security 
Imagine information security as a security guard protecting a vault. The guard secures everything valuable inside, including cash (digital data), documents (physical records), and jewels (intellectual property).
Cybersecurity, on the other hand, is like a high-tech security system installed within the vault. It focuses on protecting the digital assets stored electronically within the vault.
In summary:
Information security is the overarching concept that encompasses all aspects of information protection. Cybersecurity is a subset of information security that deals specifically with protecting information in electronic systems.

- **Qualified Security Assessor (QSA)** is an individual or organization certified by the Payment Card Industry Security Standards Council (PCI SSC) to assess compliance with the Payment Card Industry Data Security Standard (PCI DSS). The role of a QSA in compliance validation is to evaluate an organization's adherence to the PCI DSS requirements, conduct on-site assessments, validate security controls, and provide a comprehensive report on compliance status.
- **Gap analysis** is a method of assessing the performance of a business unit to determine whether business requirements or objectives are being met and, if not, what steps should be taken to meet them
- **Site reliability engineer (SRE)** is an IT expert who uses software engineering principles to improve the reliability of software systems. SREs are responsible for the availability, performance, and scalability of software systems
- Difference Between EDR and XDR
    1. **Endpoint Detection and Response (EDR)**:
        - Focuses **only on endpoints** (e.g., laptops, servers, mobile devices).
        - Detects, investigates, and responds to threats on individual devices.
        - Provides deep visibility and control over endpoint security.
        - Example: Detecting malware or anomalous behavior on a specific server.
    2. **Extended Detection and Response (XDR)**:
        - Integrates and correlates data from **multiple sources** (endpoints, networks, servers, cloud workloads, etc.).
        - Provides a **unified view** of security threats across the environment.
        - Offers broader visibility and faster threat response.
        - Example: Correlating a malicious email (email system) with endpoint activity.
    
    ---
    
    ### Key Difference:
    
    - **EDR** is endpoint-specific; **XDR** extends coverage across the entire IT ecosystem.
    
    ### Example Tools:
    
    - **EDR** tools like **Bitdefender** primarily focus on protecting individual endpoints and detecting malicious activity specific to those devices.
    - **XDR** tools like **Palo Alto Cortex XDR** or **Trend Micro Vision One** provide a broader, integrated view across various layers (endpoints, network, server, and cloud), enabling more comprehensive threat detection and response across your entire IT environment.

- **What is OPA (Open Policy Agent)?**
    
    **Open Policy Agent (OPA)** is an open-source policy engine that allows you to define, enforce, and manage policies as code. It helps in **authorization, compliance, and governance** across cloud-native environments. OPA is commonly used for **Kubernetes, microservices, API security, and infrastructure policies**.
    
    ### How OPA Works?
    
    1. A Service Sends a Query to OPA
        - Example: "Can user X access resource Y?"
    2. OPA Evaluates the Query Against Policies
        - Policies are written in Rego, checking conditions.
    3. OPA Returns a Decision
        - Example: Allow or Deny

- **What is Falco?**
    
    Falco is an open-source runtime security tool for Kubernetes, containers, and cloud environments. It detects suspicious activities, unexpected behavior, and security threats in real time by monitoring system calls (syscalls).
    
    ---
    
    ### **Why Use Falco?**
    
    ✔️ **Real-time threat detection** – Alerts when suspicious activities occur.
    
    ✔️ **Kubernetes-native** – Monitors pods, containers, and Kubernetes API events.
    
    ✔️ **Customizable rules** – Define your own security policies.
    
    ✔️ **Low overhead** – Uses eBPF/syscall monitoring for efficiency.
    
    ✔️ **Integrations** – Works with **Prometheus, Grafana, ELK, SIEMs**, etc.
    
    ---
    
    ### **How Falco Works?**
    
    1. **Intercepts system calls** (via eBPF or kernel modules).
    2. **Applies security rules** (e.g., detecting exec calls inside containers).
    3. **Generates alerts** (logs, Slack, webhook, SIEM, etc.).
    
    📌 **Example Threats Detected by Falco:**
    
    - A shell running inside a container (`bash`, `sh`).
    - Changes to system files (`/etc/passwd`, `/etc/shadow`).
    - Network activity from unexpected sources.
    - Kubernetes API misuse (e.g., creating privileged pods).
    
    ---
    
    ### **Falco in Kubernetes**
    
    Falco can monitor:
    
    ✅ Containers running as root.
    
    ✅ Privileged escalations.
    
    ✅ Host file system modifications from containers.
    
    ✅ Kubernetes API events (e.g., exec into a pod).
    

- Terms to use and topics to keep in mind
    
    We have to keep in mind the following for data:
    Security and compliance
    Performance and scalability
    Automated patching and upgrades
    Data durability and redundancy
    Monitoring and alerting
    Backup and recovery
    
    Some words to use
    Reduced operational overhead
    
    tracking aws services 
    
    monitoring aws resources 
    
    point is that for services we track and use service like aws config and cloud trail while for resources like ec2 and s3 or lambda we monitor them like metrics and logs using services like AWs cloudwatch or third party tools 
    

- **ETL (Extract, Transform, Load)**
    
    Imagine you own a **restaurant** and you get fresh **ingredients** from different suppliers (markets, farms, and grocery stores). Before serving the food to customers, you follow three main steps:
    
    1. **Extract** – Collect raw ingredients from suppliers.
    2. **Transform** – Clean, chop, and cook them into delicious meals.
    3. **Load** – Serve the final dishes to customers.
    
    This is exactly how ETL works in **data processing**!
    
    ---
    
    ### **What is ETL?**
    
    ETL is a **data integration process** used to collect (extract) data from multiple sources, modify it (transform), and store it (load) in a **central database or data warehouse**.
    
    ✅ **Extract** → Retrieve raw data from different sources (databases, APIs, spreadsheets).
    
    ✅ **Transform** → Clean, format, and process data (remove duplicates, change formats).
    
    ✅ **Load** → Store processed data into a **data warehouse** for analysis.
    
    ---
    
    ### **💡 Real-World Example**
    
    🔹 **Scenario:** A company collects customer orders from different platforms (Amazon, Shopify, eBay).
    
    🔹 **ETL Process:**
    
    - **Extract** → Pull data from Amazon, Shopify, and eBay databases.
    - **Transform** → Convert all order details into a common format, clean errors, and calculate sales trends.
    - **Load** → Store the cleaned data into a **centralized database** for reporting.
    
    ---
    
    ### **🛠️ ETL Tools**
    
    🔹 **Popular ETL Tools:**
    
    - **AWS Glue** (Cloud-based ETL for AWS users)
    - **Apache NiFi** (Open-source data integration)
    - **Talend** (Drag-and-drop ETL tool)
    - **Microsoft SSIS** (ETL tool in SQL Server)

# ISO 27000 Family: A Breakdown

![image.png](Concepts%202193e043159d819a8333d6485cba16d5/image%201.png)

---

- The ISO/IEC 27000 family is a set of standards published by the International Organization for Standardization (ISO) and the International Electrotechnical Commission (IEC) that provide a comprehensive framework for information security management. Here's a breakdown of what you need to know:

ISO 27000:
This is the foundation standard that provides an overview of information security management systems (ISMS) and the core concepts involved. It outlines the benefits of implementing an ISMS and doesn't provide specific requirements.

ISO 27001:
This is the most important standard in the family. It outlines the specific **requirements for implementing, maintaining, and continually improving an ISMS**. Earning an ISO 27001 certification demonstrates your organization's commitment to information security best practices.

ISO 27002 - 27005:
These standards **provide guidance on implementing information security controls**. They don't set mandatory requirements but **offer best practices for various information security aspects like risk management, access control, and security incident management.**

ISO 27006 - 27017:
These standards focus on specific implementation aspects. For instance, ISO 27006 provides guidance on how to conform an ISMS with national or international laws, while ISO 27017 offers best practices for information security controls for **cloud services.**

ISO 27018 - 27019:
These standards address information security for specific industries or purposes. ISO 27018 provides guidance **for protecting personally identifiable information (PII)** in cloud storage, while 
ISO 27019 focuses on information security controls for protecting personal data in the healthcare sector.
    
    **ISO 27001:2013** is a well-respected international information security standard that outlines the key processes and approaches a business needs to manage information security risk in a practical way.
    
- **ISO/IEC 27035: Your Incident Response Playbook**
    
    **ISO/IEC 27035** is an international standard that provides guidelines for managing information security incidents. It's essentially a playbook for organizations to follow when facing a security breach or other cyber incident.
    In essence, ISO/IEC 27035 provides a structured approach to handling information security incidents, helping organizations protect their assets and reputation
    
- **ISO/IEC 27034: Securing Your Applications**
    
    **ISO/IEC 27034** is a set of standards focused on **application security**. It provides guidance on how organizations can secure their applications throughout their entire lifecycle, from design and development to deployment and maintenance.
    
    **Key Goals of ISO/IEC 27034:**
    
    **Secure Development Lifecycle (SDLC):** Integrating security into every phase of the application development process.
    
    **Risk Management:** Identifying, assessing, and mitigating security risks associated with applications.
    
    **Control Implementation:** Implementing appropriate security controls to protect applications and data.
    
    **Continuous Improvement:** Regularly reviewing and enhancing application security practices.
    

- ISMS stands for Information Security Management System. It's a systematic( **structured and organized)**  approach to managing and protecting an organization's information assets.
System Goal: Protect confidentiality (privacy), integrity (accuracy), and availability of information.
Steps:
Identify risks (hacking, leaks, loss)
Make a plan with controls (passwords, firewalls, backups, training)
Implement the plan
Review and update regularly
Benefits:
Reduces security breaches
Improves overall security
Helps with compliance
Builds customer trust

# PCI DSS

( Payment Card Industry Data Security Standard )

- PCI DSS stands for **Payment Card Industry Data Security Standard**. It's a set of security requirements designed to ensure all organizations that process, store or transmit credit card information maintain a secure environment. Imagine it as a rulebook for businesses that handle credit card data, outlining essential security practices to minimize the risk of fraud and data breaches.
OR
The Payment Card Industry Data Security Standard (PCI-DSS) is a globally recognized set of requirements intended to secure and strengthen payment card transaction systems. It is applicable to all entities involved in payment card processing—including merchants, processors, acquirers, issuers, and service providers.

PCI DSS applies to all merchants and service providers that process, transmit or store cardholder data. if an organization handles card payments, it must comply — or risk suffuring from penalties. 
it was launched in 2004
- an acquirer refers to a **financial institution that has a contractual agreement with a merchant to process credit card payments**. They are essentially the receiving end of credit card transactions initiated by the merchant.
 Think of acquirers as the middlemen in the credit card world, ensuring smooth and secure transactions for both you (merchant) and your customers.

# SCADA/ICS

- **SCADA** stands for **Supervisory Control and Data Acquisition**. It's a system of software and hardware components that allows organizations to control and monitor industrial processes.
**Think of it as a digital brain for industrial operations.
Supervisory control** refers to computer systems that remotely monitor and control facility processes.
**Data acquisition** is the process of sampling signals that measure real-world physical conditions and converting the resulting samples into digital numeric values that can be manipulated by a computer.

****What does SCADA do?
    
    **Collects data:** Gathers information from various machines and sensors.
    
    **Monitors processes:** Tracks the performance of industrial processes.
    
    **Controls equipment:** Allows operators to adjust and control machinery remotely.
    
    **Visualizes data:** Presents information in a user-friendly format (like graphs and charts).
    
    **Alerts for issues:** Notifies operators of any problems or abnormalities.
    
    SCADA systems are a combination of hardware, software, and networking elements working together to achieve specific industrial goals.
    
    https://opcfoundation.org/resources/case-studies/
    You can learn alot from here 
    
- **Modbus**:
A Communication Protocol for Industrial Devices
**Modbus** is a widely used industrial communication protocol that enables different devices to communicate with each other.
**Key Features of Modbus:
Client-server architecture:** One device (the master) initiates communication and requests data from other devices (slaves).
**Open standard:** It's freely available for use by anyone, promoting compatibility and interoperability.
**Multiple versions:** Modbus supports various physical layers (serial, Ethernet) and data encoding methods (RTU, ASCII, TCP/IP).
- OT ( operational technology )
**Operational Technology (OT)** is essentially the hardware and software used to control and monitor physical devices and processes in industrial settings. It's the technology that makes things happen in the real world.
Examples of OT:
    
    **Industrial control systems (ICS):** These are systems that control industrial processes, such as manufacturing, oil and gas production, and power generation.
    
    **Supervisory control and data acquisition (SCADA) systems:** These systems monitor and control industrial processes from a central location.
    
    **Programmable logic controllers (PLCs):** These are computer-based controllers used to automate industrial processes.
    
    **Robots:** These are programmable machines used to perform tasks that would otherwise be done by humans.
    
    **Key differences between OT and IT:**
    
    **Purpose:** OT focuses on controlling physical processes, while IT focuses on managing information.
    
    **Environment:** OT systems often operate in harsh environments, while IT systems are typically in controlled environments.
    
    **Security:** OT systems have traditionally had weaker security measures compared to IT systems.
    
    **Reliability:** OT systems require high levels of reliability and uptime, as failures can have significant consequences.
    

# CIS Top 20 Controls: A Brief Overview

- **CIS Top 20 Controls** is a cybersecurity framework developed by the Center for Internet Security (CIS). It provides a prioritized set of actions that organizations can take to defend against cyber threats. These controls are designed to be applicable across various industries and organization sizes.
- **1. Inventory and Control of Enterprise Assets**: Actively manage (inventory, track, and correct) all enterprise assets connected to the infrastructure physically, virtually, remotely, and those within cloud environments.
- **2. Inventory and Control of Software Assets**: Actively manage (inventory, track, and correct) all software on the network so that only authorized software is installed and can execute.
- **3. Data Protection**: Manage the data lifecycle and protect the organization’s most critical information.
- **4. Secure Configuration of Enterprise Assets and Software**: Establish and maintain the secure configuration of enterprise assets (endpoints, servers, network devices, etc.) and software.
- **5. Account Management**: Use processes and tools to create, assign, manage, and disable accounts as necessary.
- **6. Access Control Management**: Use processes and tools to assign access based on the principle of least privilege and ensure proper separation of duties.
- **7. Continuous Vulnerability Management**: Continuously acquire, assess, and take action on information regarding new software vulnerabilities.
- **8. Audit Log Management**: Collect, alert, review, and retain audit logs of events that could help detect, understand, or recover from an attack.
- **9. Email and Web Browser Protections**: Improve protections and security for email and web browsers.
- **10. Malware Defenses**: Control the installation, spread, and execution of malicious code at multiple points in the enterprise.
- **11. Data Recovery**: Implement and test data recovery processes to ensure the ability to restore data.
- **12. Network Infrastructure Management**: Implement network-based measures to enhance security.
- **13. Security Awareness and Skills Training**: Implement a security awareness program to foster a security-conscious workforce.
- **14. Service Provider Management**: Develop processes to manage service providers who hold sensitive data.
- **15. Application Software Security**: Incorporate security into the software development lifecycle.
- **16. Incident Response Management**: Develop and test processes to respond to and manage cybersecurity incidents.
- **17. Penetration Testing**: Regularly test security controls via penetration testing to identify vulnerabilities.
- **18. Security Monitoring**: Implement monitoring measures to identify and respond to security events.
- **19. Secure Configuration for Network Devices**: Establish and maintain secure configurations for network infrastructure devices.
- **20. Wireless Access Control**: Manage wireless access points to secure unauthorized access.
- IS Top 20 Controls (Simplified)
    
    **Note:** This is a very simplified overview. Each control has many details and steps involved.
    
    you will have to audit an organization’s controls  and match the cis tp 20 
    
    for example in alnafi top 20 controls course they had an audit tool in exel where there where controls and then they would check if the control has a policy written, partially written etc and if it is implemented, automated or manually executed etc and then they would check the score for risk accepted.
    
    ![Untitled](Concepts%202193e043159d819a8333d6485cba16d5/Untitled%203.png)
    
    # **Elasticsearch Threat Hunting & Observability Engineer**
    
    - **Elasticsearch Threat Hunting & Observability Engineer** is a cybersecurity professional who specializes in using the Elasticsearch platform to detect, investigate, and respond to cyber threats. They also ensure the smooth operation and optimization of the platform for observability purposes.
    
    **Breaking Down the Terms
    Elasticsearch:** A powerful, open-source search and analytics engine used to store, search, and analyze large volumes of data. It's a core component of the Elastic Stack, often used for log management, application performance monitoring, and security analytics.
    
    **Threat Hunting:** A proactive cybersecurity strategy involving the in-depth examination of networks and systems to uncover hidden threats that have evaded detection by traditional security tools.
    
    **Observability:** The ability to understand the internal state of a system based on its external outputs. It involves collecting and analyzing data from different sources to gain insights into system performance, behavior, and health.
    Observability is **the ability to monitor, measure, and understand the state of a system or application**
    - Differnece Between SOC And ElasticSearch 
    **Focus**
        - Elasticsearch Threat Hunting & Observability Engineer: Elasticsearch, threat hunting, observability
        - SOC: Security monitoring, incident response, threat management
        
        **Scope**
        
        - Elasticsearch Threat Hunting & Observability Engineer: Specialized role within a larger security team
        - SOC: Broader team responsible for overall security operations
        
        **Activities**
        
        - Elasticsearch Threat Hunting & Observability Engineer: Data analysis, query development, cluster optimization
        - SOC: Incident response, threat intelligence, security automation
        
        To illustrate the relationship, imagine a SOC as a hospital. The SOC is responsible for the overall patient care (security operations), while the Elasticsearch engineer is a specialist radiologist (focused on a specific tool and skill set) who helps diagnose and treat patients (threats).
        
    - **Elastic Agent**
    is a single, unified agent that simplifies the process of collecting and sending various types of data to Elasticsearch.
    It replaces the need for multiple agents or manual configuration for different data sources.
    - **The Company:** Elastic is a technology company that develops and sells the Elastic Stack, a suite of open-source software products
    - **Product Suite:** The Elastic Stack includes Elasticsearch, Logstash, Kibana, Beats, and other related products.
    - **Commercial Offerings:** Elastic also offers commercial versions of its software with additional features and support.
    - Elasticsearch, Kibana, Logstash, and Beats are components of the Elastic Stack. **Elasticsearch is a powerful search and analytics engine**, while **Logstash is used to collect, process, and transform data.** **Beats are lightweight data shippers that can send data to Logstash or Elasticsearch**. Kibana, on the other hand, is a **powerful data visualization and management tool that can be used to add, explore, visualize, present, and share your data**. With Kibana, you can create interactive dashboards and visualizations, perform advanced data analysis, and monitor your Elastic Stack in real time.
    
    ### **XDR**, **SIEM**, **SOAR**, & **EDR**
    
    ---
    
    ### **1. XDR (Extended Detection and Response)**
    
    **What It Is:**
    
    - XDR is a security solution that integrates multiple security tools (like antivirus, firewalls, and email security) to provide a unified approach to detecting and responding to threats across an organization.
    
    **Simple Explanation:**
    
    - Think of XDR as a central hub that connects all your security tools, allowing them to share information and work together to spot and handle threats more effectively.
    
    **Use Case Example:**
    
    - **Scenario:** A company uses antivirus software on all its computers, a firewall to protect its network, and an email security tool to filter out spam.
    - **How XDR Helps:** XDR connects these tools so that if the antivirus detects a suspicious file, the firewall can automatically block any related network traffic, and the email tool can quarantine any related emails. This coordinated response helps stop the threat quickly before it spreads.
    
    ---
    
    ### **2. SIEM (Security Information and Event Management)**
    
    **What It Is:**
    
    - SIEM is a system that collects and analyzes data from various sources within an organization’s IT environment to detect and respond to potential security threats.
    
    **Simple Explanation:**
    
    - SIEM acts like a security camera system that not only records what’s happening but also analyzes the footage to identify any unusual or suspicious activities.
    
    **Use Case Example:**
    
    - **Scenario:** A company has servers, workstations, and network devices all generating logs of their activities.
    - **How SIEM Helps:** SIEM collects these logs in one place and analyzes them to detect patterns that might indicate a security breach, such as multiple failed login attempts or unusual data transfers. When such patterns are detected, SIEM alerts the security team to investigate further.
    
    ---
    
    ### **3. SOAR (Security Orchestration, Automation, and Response)**
    
    **What It Is:**
    
    - SOAR is a set of tools and processes that help automate and coordinate responses to security incidents, making it easier and faster to handle threats.
    
    **Simple Explanation:**
    
    - SOAR is like an automated assistant for your security team. It takes care of routine tasks and coordinates different tools so the team can focus on more complex issues.
    
    **Use Case Example:**
    
    - **Scenario:** A company receives an alert about a potential phishing email.
    - **How SOAR Helps:** SOAR automatically performs the following actions:
        1. **Orchestration:** Coordinates between email security, antivirus, and user management systems.
        2. **Automation:** Automatically quarantines the suspicious email, scans the affected user's computer for malware, and resets the user's password.
        3. **Response:** Generates a report for the security team, summarizing the actions taken and any further steps needed.
    - **Benefit:** This rapid, automated response helps contain the threat quickly without manual intervention, reducing the risk of a successful attack.
    
    ---
    
    ### **4. EDR (Endpoint Detection and Response)**
    
    **What It Is:**
    
    - EDR focuses on monitoring and protecting individual devices (endpoints) like computers, laptops, and mobile devices from cyber threats.
    
    **Simple Explanation:**
    
    - EDR is like having a security guard on each of your devices, constantly watching for suspicious activities and taking action if something bad happens.
    
    **Use Case Example:**
    
    - **Scenario:** An employee’s laptop starts behaving unusually, showing signs of a malware infection.
    - **How EDR Helps:**
        1. **Detection:** EDR detects unusual behavior, such as unexpected file changes or unauthorized access attempts.
        2. **Response:** EDR isolates the laptop from the network to prevent the malware from spreading.
        3. **Investigation:** EDR provides detailed information about the threat, helping the IT team understand how the malware entered the system and how to remove it.
    - **Benefit:** By quickly detecting and responding to threats on individual devices, EDR helps prevent malware from spreading and causing more significant damage.
    
    ---
    
    ### **Summary Table**
    
    | **Tool** | **What It Is** | **Simple Explanation** | **Use Case Example** |
    | --- | --- | --- | --- |
    | **XDR** | Integrates multiple security tools for unified threat detection and response. | A central hub connecting all security tools to spot and handle threats effectively. | Combines antivirus, firewall, and email security to automatically block and quarantine threats. |
    | **SIEM** | Collects and analyzes security data from various sources to detect threats. | A security camera system that records and analyzes activities to identify suspicious actions. | Aggregates logs from servers and devices to detect patterns like multiple failed logins and alerts the security team. |
    | **SOAR** | Automates and coordinates responses to security incidents. | An automated assistant that handles routine security tasks and coordinates tools for the security team. | Automatically quarantines phishing emails, scans for malware, resets passwords, and generates reports. |
    | **EDR** | Monitors and protects individual devices from cyber threats. | A security guard on each device that watches for suspicious activities and takes action. | Detects malware on a laptop, isolates it from the network, and provides details for removal and investigation. |
    
    ---
    
    ### **Key Takeaways**
    
    - **XDR** provides a comprehensive view by integrating various security tools to enhance threat detection and response.
    - **SIEM** centralizes and analyzes security data to identify potential threats across the entire network.
    - **SOAR** automates and coordinates incident responses, making security operations more efficient.
    - **EDR** focuses on protecting individual devices by monitoring their activities and responding to threats promptly.
    
    These tools work together to create a robust security infrastructure, helping organizations detect, respond to, and mitigate cyber threats effectively.
    
    ### **Logs**, **Traces**, and **Metrics**.
    
    ---
    
    ### **Logs**:
    
    - **Text Form**: Logs are plain text records of events.
    - **Timestamp**: Indicates when the log entry occurred.
    - **Message**: Contains useful information about the event.
    
    **Example**:
    
    ```jsx
    2024-09-20 12:45:30 - Error: Application crashed.
    ```
    
    ---
    
    ### **Traces**:
    
    - **Start Time**: The time when a request or transaction began.
    - **Duration**: How long it took to complete the request.
    - **Parent ID**: Used to track how different services interact in a distributed system.
    
    **Example**:
    
    ```yaml
    Trace ID: 123, Start: 12:45:30, Duration: 150ms, Parent ID: 456
    ```
    
    ---
    
    ### **Metrics**:
    
    - **Metric Name**: Identifies what is being measured (e.g., CPU usage).
    - **Value**: The measured value at a specific time.
    - **Timestamp**: When the metric was recorded.
    - **Duration**: The period the metric covers, if applicable.
    
    **Example**:
    
    ```yaml
    Metric: CPU_Usage, Value: 85%, Timestamp: 12:45:3
    ```
    
    ---
    
    ### **Summary**:
    
    - **Logs**: Record events with timestamps and messages.
    - **Traces**: Track requests and their duration across services.
    - **Metrics**: Measure system performance using key values over time.
    
    Effective observability ensures you can monitor, troubleshoot, and improve system performance in real time.