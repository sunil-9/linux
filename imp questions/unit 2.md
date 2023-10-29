## 1. What is linux file System? Explain file system hierarchy with their special purposes in linux.

The Linux file system is a hierarchical structure used to organize and manage files, directories, and other data on a Linux-based operating system. It provides a unified way to access, store, and manage data, and it plays a crucial role in the overall functionality of the system. The Linux file system adheres to a standard hierarchy known as the Filesystem Hierarchy Standard (FHS), which defines the layout and purposes of various directories.

Here's an explanation of the key directories in the Linux file system hierarchy and their special purposes:

![](file-stucture.webp)

1. **/ (Root Directory):**

   - The root directory is the top-level directory in the Linux file system hierarchy. It serves as the starting point for the entire directory tree.
   - Special Purpose: It contains essential system files, configurations, and subdirectories that organize the entire file system.

2. **/bin (Binary Binaries):**

   - The /bin directory contains essential system binaries and commands that are required for system recovery and repair, even if other file systems are not mounted.
   - Special Purpose: It contains fundamental command-line utilities necessary for system maintenance and recovery.

3. **/sbin (System Binaries):**

   - Similar to /bin, the /sbin directory holds system binaries and commands, but these are intended for administrative or system maintenance tasks.
   - Special Purpose: It contains utilities used by the system administrator for system configuration and recovery.

4. **/etc (System Configuration):**

   - The /etc directory stores system-wide configuration files and scripts, which configure various aspects of the operating system and installed software.
   - Special Purpose: It contains critical configuration files for system services, network settings, user authentication, and more.

5. **/lib (Library Files):**

   - The /lib directory contains shared library files (shared objects) that are essential for the operation of programs and system utilities.
   - Special Purpose: It stores dynamic link libraries required by various executables to run properly.

6. **/usr (User Binaries and Data):**

   - The /usr directory is a major subdirectory that contains user-specific data, executables, and libraries.
   - Special Purpose: It houses most of the system's user-related binaries, libraries, documentation, and data, making it one of the largest directories in the file system.

7. **/var (Variable Data):**

   - The /var directory holds variable data, such as log files, spool directories, mail, and other files that may change in size over time.
   - Special Purpose: It is used to store data that can change during system operation. For example, system logs are located in /var/log.

8. **/tmp (Temporary Files):**

   - The /tmp directory serves as a location for temporary files created by applications and users. These files are typically deleted upon system reboot.
   - Special Purpose: It provides a space for short-lived temporary files used by running processes.

9. **/home (User Home Directories):**

   - The /home directory contains user home directories where users store their personal files, documents, and configurations.
   - Special Purpose: Each user has a dedicated directory here to manage their files and settings.

10. **/mnt (Mount Point):**

    - The /mnt directory is used as a mount point for temporarily mounting external devices, such as USB drives or network shares.
    - Special Purpose: It provides a location to access and interact with external storage devices.

11. **/boot (Boot Files):**

    - The /boot directory contains files required for the system's bootloader and kernel initialization.
    - Special Purpose: It stores the bootloader configuration and the kernel image used during the boot process.

12. **/opt (Optional Software):**

    - The /opt directory is used to install and store optional software packages and applications not included in the base system.
    - Special Purpose: It allows for the installation of third-party or add-on software in an organized manner.

13. **/srv (Service Data):**
    - The /srv directory is intended for site-specific data and configuration files related to system services.
    - Special Purpose: It provides a location for storing data used by services such as web servers and FTP servers.

This explanation provides an overview of the most significant directories in the Linux file system hierarchy and their special purposes. Understanding this hierarchy is essential for efficient file management, system administration, and troubleshooting on a Linux system.

## 2. Define and explain Shell? What is ksh? What are the basic differences between BASH and DOS? Differentiate between TCSH and KSH?

**Shell:**
A shell is a command-line interface (CLI) or command interpreter that provides a user interface for interacting with an operating system. It is a program that takes user commands, interprets them, and then executes the requested operations. Shells are fundamental components of Unix-like operating systems, including Linux, macOS, and various Unix systems. They allow users to run commands, manage files and directories, and perform a wide range of tasks.

Shells provide features such as command-line editing, scripting capabilities, environment variables, and the ability to redirect input and output, making them versatile tools for system administrators, developers, and power users.

**Ksh (Korn Shell):**
The Korn Shell (ksh) is a Unix shell that was developed by David Korn at AT&T Bell Laboratories in the early 1980s. Ksh is an enhanced version of the original Unix Bourne Shell (sh), and it aimed to improve upon the limitations of the original shell. Ksh offers scripting capabilities, command-line editing features, and job control, making it a powerful choice for both interactive use and shell scripting. It is known for its compatibility with sh, making it a natural successor for Bourne Shell users.

**Differences Between BASH and DOS:**

| Aspect                   | BASH (Bourne-Again Shell)       | DOS (Disk Operating System)                |
| ------------------------ | ------------------------------- | ------------------------------------------ |
| **Operating System**     | Unix-like (Linux, macOS)        | MS-DOS, Windows 9x                         |
| **Command Syntax**       | Case-sensitive, space-separated | Not case-sensitive, slash/hyphen-separated |
| **File Paths**           | Forward slashes (/)             | Backslashes (\)                            |
| **Command Availability** | Extensive built-in commands     | Limited built-in commands                  |
| **Scripting**            | Powerful scripting language     | Basic scripting capabilities               |

**Differences Between TCSH and KSH:**

| Aspect              | TCSH (TENEX C Shell)                   | KSH (Korn Shell)                             |
| ------------------- | -------------------------------------- | -------------------------------------------- |
| **History**         | Enhanced Csh                           | Enhanced Bourne Shell (sh)                   |
| **Syntax**          | C-like syntax                          | C-like syntax                                |
| **Interactive Use** | User-friendly for interactive sessions | Versatile for both interactive and scripting |
| **Scripting**       | Limited scripting capabilities         | Strong scripting capabilities                |

## 3. What do you mean by booting? Define the function of following command with examples.

```
a. Is
b. du
c. chmod 741
d. top
e. touch me
f. fdisk-1
g. df-h
h. lsmod
i. ifconfig
j. cat
k. ifconfig
l. nslookup

```

**Booting:**
Booting refers to the process of starting or initializing a computer or operating system. It is the sequence of operations that take place when you turn on your computer or restart it to load the operating system into memory and prepare it for use. The term "boot" comes from "bootstrapping," a reference to the idea of lifting oneself up by one's bootstraps. During booting, the computer goes through several stages, including power-on self-test (POST), loading the BIOS or UEFI firmware, initializing hardware components, loading the operating system kernel, and finally, presenting a usable desktop or command-line interface to the user.

There are primarily two types of booting:

1. **Cold Boot (Hard Boot):** In a cold boot, the computer is powered on from a completely turned-off state. When you press the power button to start your computer, it undergoes a cold boot process, where the hardware components are initialized from scratch.

2. **Warm Boot (Soft Boot or Reboot):** In a warm boot, the computer is restarted without being powered off. This is typically done to reset the operating system or apply changes, such as installing updates or new software. When you use the "Restart" option in your operating system, it initiates a warm boot.

Now, let's define the functions of the listed commands with examples:

a. **Is (List Files and Directories):**

- **Function:** List files and directories in a directory.
- **Example:** `ls` lists the contents of the current directory.

b. **du (Disk Usage):**

- **Function:** Display the disk space used by files and directories.
- **Example:** `du -sh /path/to/directory` shows the total disk usage (human-readable format) for the specified directory.

c. **chmod 741 (Change File Permissions):**

- **Function:** Change the permissions of a file or directory.
- **Example:** `chmod 741 myfile.txt` sets the file permissions of "myfile.txt" to read, write, and execute for the owner (7), read for the group (4), and no permissions for others (1).

d. **top (System Monitoring):**

- **Function:** Display real-time system resource usage, including CPU, memory, and processes.
- **Example:** Running `top` in the terminal provides a dynamic list of processes and system statistics.

e. **touch (Create Empty File):**

- **Function:** Create an empty file or update the access and modification timestamps of an existing file.
- **Example:** `touch myfile.txt` creates an empty file named "myfile.txt."

f. **fdisk (Partition Table Manipulation):**

- **Function:** Manipulate disk partition tables.
- **Example:** `fdisk -l` lists the partitions on all available disks.

g. **df (Disk Space Usage):**

- **Function:** Display information about disk space usage on mounted file systems.
- **Example:** `df -h` shows disk space usage in a human-readable format.

h. **lsmod (List Loaded Kernel Modules):**

- **Function:** List loaded kernel modules (device drivers) in the Linux kernel.
- **Example:** `lsmod` displays a list of loaded kernel modules.

i. **ifconfig (Network Configuration):**

- **Function:** Display or configure network interfaces on Unix-like operating systems (deprecated in favor of "ip" command).
- **Example:** `ifconfig eth0` displays information about the "eth0" network interface.

j. **cat (Concatenate and Display Files):**

- **Function:** Display the contents of one or more files.
- **Example:** `cat myfile.txt` displays the contents of "myfile.txt."

k. **ifconfig (Network Configuration - Duplicate Entry):**

- **Function:** Similar to "i. ifconfig," this appears to be a duplicate entry.

l. **nslookup (DNS Query):**

- **Function:** Perform DNS (Domain Name System) queries to resolve hostnames to IP addresses and vice versa.
- **Example:** `nslookup example.com` queries DNS to find the IP address associated with "example.com."

## 4. What is the difference between absolute path and relative path? Explain with examples.

**Absolute Path vs. Relative Path:**

In file systems, both absolute and relative paths are used to specify the location of a file or directory. The key difference between them is how they reference the location:

**1. Absolute Path:**

- An absolute path specifies the complete path to a file or directory starting from the root directory (the top-level directory) of the file system.
- It provides a full and unambiguous reference to the location of a file or directory, regardless of the current working directory.
- Absolute paths always start with a forward slash (/) on Unix-like systems (Linux, macOS) and a drive letter (e.g., C:\) on Windows.
- They are typically longer and less portable, as they include the entire directory structure.
- Example (Unix-like): `/home/user/documents/myfile.txt`
- Example (Windows): `C:\Users\User\Documents\myfile.txt`

**2. Relative Path:**

- A relative path specifies the location of a file or directory relative to the current working directory.
- It is a shorter and more flexible way to reference files and directories within the context of a specific location.
- Relative paths do not start with a forward slash (/) or drive letter, as they assume the current working directory as the starting point.
- They are often used when referring to files or directories within the same project or directory structure.
- Example: If the current working directory is `/home/user/documents`, a relative path to `myfile.txt` in the same directory is simply `myfile.txt`.

**Examples:**

**1. Absolute Path Example:**

- Suppose you want to access a file named "document.txt" located in the directory "/home/user/documents":
- The absolute path to this file is `/home/user/documents/document.txt`.
- No matter where your current working directory is, this path will always lead to the same file.

**2. Relative Path Example:**

- Consider the same file, "document.txt," located in the directory "/home/user/documents," but now your current working directory is `/home/user`:
- The relative path to access the file is `documents/document.txt`.
- It starts from the current working directory (`/home/user`) and then specifies the path to the file relative to that location.
- If you change your current working directory to `/home/user/documents`, the same relative path will still correctly reference the file.

**Use Cases:**

- Use absolute paths when you need a fixed and unchanging reference to a file or directory, regardless of the current working directory. This is common in configuration files, scripts, and system settings.
- Use relative paths when you want to reference files or directories in a more flexible and portable manner within a specific project or context.

## 5. Write the purpose of following directories in Linux.

```
/home
/dev
/boot
/tmp
/root
/proc
/etc
```

Here are the purposes of the mentioned directories in Linux:

1. **/home:**

   - **Purpose:** The `/home` directory contains the home directories of user accounts. Each user typically has their own subdirectory within `/home` where they store their personal files and configurations.
   - **Usage:** It provides a secure and organized location for users to store their data, settings, and personal files.

2. **/dev:**

   - **Purpose:** The `/dev` directory contains device files that represent hardware devices and peripherals connected to the system. These files are used to interact with and access hardware resources.
   - **Usage:** Device files in `/dev` allow users and programs to communicate with hardware devices, such as hard drives, input devices, and audio devices.

3. **/boot:**

   - **Purpose:** The `/boot` directory contains the files necessary for the system's boot process. This includes the bootloader configuration, kernel files, and initial ramdisk (initrd) files.
   - **Usage:** `/boot` is essential for the booting process, as it contains the components required to load the operating system kernel and initiate the system startup.

4. **/tmp:**

   - **Purpose:** The `/tmp` directory is used for storing temporary files and directories that are created by various programs and processes. These files are typically deleted upon system reboot.
   - **Usage:** `/tmp` provides a location for applications to store temporary data that is needed only temporarily, preventing clutter in other directories.

5. **/root:**

   - **Purpose:** The `/root` directory is the home directory for the root user, also known as the superuser or system administrator. It contains configuration files and data specific to the root user.
   - **Usage:** The root user has elevated privileges and can access and modify system files and configurations. `/root` serves as the root user's home directory.

6. **/proc:**

   - **Purpose:** The `/proc` directory is a virtual filesystem that provides information about running processes and kernel parameters in real-time. It contains directories and files that represent various aspects of the system's state.
   - **Usage:** `/proc` is used by system administrators and monitoring tools to gather information about processes, hardware, and system configurations. It is not a traditional filesystem but a dynamic interface to the kernel.

7. **/etc:**
   - **Purpose:** The `/etc` directory contains system-wide configuration files and settings for various software applications and services. It stores configuration data for system processes, libraries, and system-wide settings.
   - **Usage:** `/etc` is a critical directory for system configuration. It allows administrators to customize system behavior, network settings, security policies, and more.

## 6. How can you determine the total memory used by LINUX? Why Linux is considered as more secured than other operating systems

To determine the total memory used by a Linux system, you can use various commands and tools. One commonly used command is `free`. Here's how you can use it:

1. Open a terminal on your Linux system.

2. Run the following command to display memory usage information:

   ```
   free -h
   ```

   - The `-h` option makes the output human-readable, showing memory values in a more user-friendly format.

3. The output will include information about total memory (RAM), used memory, free memory, and more. Look for the "total" row under the "Mem" section to find the total memory in use.

   Example output:

   ```
                total        used        free      shared  buff/cache   available
   Mem:          15Gi       3.0Gi       7.4Gi       172Mi       4.3Gi        11Gi
   Swap:         15Gi          0B        15Gi
   ```

> In this example, the total RAM is approximately 15 gigabytes (GiB).

Linux is often considered more secure than certain other operating systems for several reasons:

1. **Open Source:** Linux is open-source software, which means that its source code is freely available and can be reviewed and audited by anyone. This transparency allows the community to identify and fix security vulnerabilities quickly.

2. **Security Features:** Linux includes robust security features, such as user and group permissions, discretionary access control (DAC), mandatory access control (MAC), and capabilities. These features help restrict access to system resources and data.

3. **Regular Updates:** Linux distributions provide regular security updates and patches to address known vulnerabilities. Users can easily update their systems to stay protected.

4. **Community Support:** The Linux community is vast and active. Users and developers collaborate to address security issues promptly and share security best practices.

5. **Customization:** Linux allows users to customize their systems to suit their security needs. This flexibility enables administrators to implement security policies tailored to their requirements.

6. **Strong Authentication:** Linux supports various authentication methods, including password-based, key-based (SSH), and multi-factor authentication (MFA), enhancing user authentication and access control.

7. **Minimal Attack Surface:** Linux distributions typically have minimal installation footprints, which reduce the potential attack surface. Unnecessary services and applications are often disabled by default.

8. **Network Security:** Linux includes powerful firewall tools like iptables and firewalld, which allow administrators to define network access rules and enhance network security.

9. **Community Auditing:** The large Linux user base, along with security experts and organizations, continuously audits and tests Linux distributions for vulnerabilities.

10. **Centralized Package Management:** Most Linux distributions use centralized package management systems (e.g., APT, YUM) to install and update software. This ensures that software is obtained from trusted sources.

## 7. Write the function of following command with example.

`rpm -i, fdisk -1,at, iptables, alias, chgrp, chmod, man, pstree,nslookup`


1. **rpm -i**: The `rpm` command is used for managing packages in RPM-based Linux distributions. The `-i` option stands for "install," and it is used to install a package. You typically provide the name of the RPM package as an argument.

   Example: `rpm -i package.rpm`

2. **fdisk**: The `fdisk` command is used for disk partitioning on Linux. It allows you to create, delete, and manage disk partitions on your system.

   Example: `fdisk /dev/sda`

3. **at**: The `at` command is used to schedule one-time tasks to be executed at a specified time in the future.

   Example: `at 3:00 PM < script.sh`

4. **iptables**: The `iptables` command is used for configuring and managing firewall rules on Linux systems.

   Example: `iptables -A INPUT -p tcp --dport 80 -j ACCEPT`

5. **alias**: The `alias` command is used to create shortcuts (aliases) for other commands. It allows you to define custom command names or abbreviations.

   Example: `alias ll='ls -l'`

6. **chgrp**: The `chgrp` command is used to change the group ownership of a file or directory.

   Example: `chgrp users myfile.txt`

7. **chmod**: The `chmod` command is used to change the permissions (read, write, execute) of files and directories.

   Example: `chmod 755 script.sh`

8. **man**: The `man` command is used to display manual pages for other commands and utilities. It provides detailed documentation and usage instructions.

   Example: `man ls`

9. **pstree**: The `pstree` command displays the processes on your system in a hierarchical tree format, showing parent-child relationships between processes.

   Example: `pstree`

10. **nslookup**: The `nslookup` command is used for querying DNS (Domain Name System) servers to look up IP addresses or domain information.

    Example: `nslookup example.com`