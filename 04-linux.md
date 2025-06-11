### **What is Linux?**  
Linux is an open-source operating system (OS) based on the Unix architecture. It is widely used for servers, desktops, mobile devices, and embedded systems due to its stability, flexibility, and security. The Linux OS consists of the **Linux kernel** (core system) and various software and tools provided by Linux distributions.  

Linux is a family of open-source, Unix-like operating systems that are built on the Linux kernel. The kernel, initially developed by Linus Torvalds, was first released on September 17, 1991.

---

### **Why Use Linux?**  
1. **Open Source**: Free to use, modify, and distribute.  
2. **Security**: Robust against malware and viruses due to strong permissions and active community updates.  
3. **Stability**: Reliable for servers, databases, and mission-critical tasks.  
4. **Flexibility**: Customizable to fit specific use cases—servers, desktops, IoT, etc.  
5. **Community Support**: Backed by a large community offering solutions and regular updates.  
6. **Cost-Effective**: No licensing fees, reducing overall costs.  
7. **Performance**: Efficient use of resources, making it ideal for both low-end and high-end systems.  
8. **Cross-Platform**: Runs on a wide range of hardware, from embedded devices to supercomputers.  

---

### **What Does Open Source Mean?**  
Open Source refers to software whose source code is freely available for anyone to view, modify, and distribute.  
**Key Characteristics**:  
- **Transparency**: Source code is accessible.  
- **Collaboration**: Encourages contributions from developers worldwide.  
- **Customization**: Freedom to adapt software to individual needs.  
- **Free Distribution**: Redistribution without legal or financial barriers.  
Examples: Linux, Apache, MySQL, Kubernetes.  

---

### **Where to Download the Linux Kernel Source Code?**  
The Linux kernel source code is hosted on the official website and version control platforms.  
1. **Official Website**: [kernel.org](https://www.kernel.org)  
2. **Git Repository**:  
   ```bash
   git clone https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
   ```
   Developers can download, explore, or contribute to the Linux kernel.  

---

### **Linux Distributions**  
A **Linux Distribution (Distro)** combines the Linux kernel with additional software (desktop environments, package managers, utilities, etc.) to provide a complete OS tailored for different use cases.  

#### **Popular Linux Distributions**  
1. **General Use**:  
   - Ubuntu  
   - Fedora  
   - Linux Mint  
   - Manjaro  

2. **Enterprise Servers**:  
   - Red Hat Enterprise Linux (RHEL)  
   - SUSE Linux Enterprise Server (SLES)  
   - Oracle Linux  

3. **Community Servers**:  
   - CentOS Stream  
   - Rocky Linux  
   - AlmaLinux  

4. **Developers**:  
   - Arch Linux  
   - Debian  

5. **Penetration Testing**:  
   - Kali Linux  
   - Parrot OS  

6. **Lightweight Systems**:  
   - Puppy Linux  
   - Lubuntu  

7. **IoT and Embedded Systems**:  
   - Raspbian (for Raspberry Pi)  
   - Yocto Project  

Each distribution caters to specific needs, making Linux versatile and widely adopted.

---

### **Linux Directory Structure Overview**
The Linux file system is organized hierarchically, with `/` as the root. Each directory has a specific purpose, ensuring clear separation of system, user, and software files. Understanding these directories helps in managing and troubleshooting Linux systems effectively.

---

#### **1. `/` (Root Directory):**  
- **Purpose**: The top-level directory, the parent of all other directories.  
- **Analogy**: Similar to `C:\` in Windows.  
- **Key Note**: Everything in Linux starts from this root directory.

---

#### **2. `/root` (Root User’s Home Directory):**  
- **Purpose**: The home directory for the root user (superuser).  
- **Analogy**: Equivalent to `C:\Users\Administrator` in Windows.  
- **Key Note**: Provides a private workspace for the root user.

---

#### **3. `/home` (Users' Home Directory):**  
- **Purpose**: The home directory for regular (non-root) users.  
- **Analogy**: Equivalent to `C:\Users\<username>` in Windows.  
- **Key Note**: Each user gets a subdirectory within `/home`.

---

#### **4. `/bin` (Binary Executables):**  
- **Purpose**: Contains essential binary files used by all users (e.g., `ls`, `cp`, `mv`).  
- **Key Note**: Commands in `/bin` are available in single-user mode and are critical for system operation.

---

#### **5. `/boot` (Boot Loader Files):**  
- **Purpose**: Contains the Linux kernel, boot configuration, and related files.  
- **Key Note**: Essential for starting the OS (e.g., `vmlinuz`, `grub`).

---

#### **6. `/dev` (Device Files):**  
- **Purpose**: Contains files that represent hardware devices like hard disks (`/dev/sda`) or CD-ROMs (`/dev/cdrom`).  
- **Analogy**: Similar to **Device Manager** in Windows.  
- **Key Note**: Provides an interface to interact with devices.

---

#### **7. `/etc` (Configuration Files):**  
- **Purpose**: Stores system-wide configuration files (e.g., `/etc/passwd`, `/etc/resolv.conf`).  
- **Key Note**: Critical for system settings and service management.

---

#### **8. `/usr` (User Programs):**  
- **Purpose**: Contains user-level programs and libraries (e.g., installed software).  
- **Analogy**: Similar to `C:\Program Files` in Windows.  
- **Key Note**: It includes subdirectories like `/usr/bin`, `/usr/lib`, and `/usr/share`.

---

#### **9. `/sbin` (System Binaries):**  
- **Purpose**: Contains system administration commands (e.g., `ifconfig`, `iptables`).  
- **Key Note**: Only root or superusers can execute commands here.

---

#### **10. `/var` (Variable Files):**  
- **Purpose**: Contains data that changes frequently (e.g., logs, databases).  
- **Examples**:  
  - Log files: `/var/log/messages`  
  - Databases: `/var/lib/mysql`  
- **Key Note**: Used for data that grows dynamically.

---

#### **11. `/mnt` (Mount Points):**  
- **Purpose**: Temporary mount point for file systems.  
- **Key Note**: Empty by default, used for manual mounting.

---

#### **12. `/media` (Removable Media):**  
- **Purpose**: Mount point for removable media (e.g., USB, CDs).  
- **Key Note**: Automatically used by the system for devices like pen drives.

---

#### **13. `/lib` and `/lib64` (Library Files):**  
- **Purpose**: Contains essential shared libraries used by programs.  
- **Analogy**: Similar to `.dll` files in Windows.  
- **Key Note**: Library files have `.so` (Shared Object) extensions.

---

#### **14. `/proc` (Process Information):**  
- **Purpose**: A virtual directory containing runtime system information (e.g., processes, RAM, CPU).  
- **Key Note**: Its contents change dynamically based on system state.

---

#### **15. `/opt` (Optional Software):**  
- **Purpose**: Contains optional third-party software and add-ons.  
- **Key Note**: A separate directory is created for each software package.

---

### **Linux Commands Quick Reference**

---

#### **Environment and User Commands:**
1. **`env`**: Displays all the environment variables for the current user.  
2. **`whoami`**: Shows the current user.  

---

#### **System and Information Commands:**

**`hostname`**: Displays the current system's hostname — the name assigned to the machine.
Example: `hostname` → might return `ip-172-31-0-23`

**`cat /etc/os-release`**: Shows detailed operating system info such as name, version, and ID.
Useful for confirming if you're running Amazon Linux 2023 or another distro.

**`hostnamectl`**: Provides complete hostname details and system metadata like OS, kernel, and architecture.
Also used to change the hostname with `sudo hostnamectl set-hostname newname`.

**`uptime`**: Shows how long the system has been running, number of users, and load averages.
Example: `uptime` → `10:45:01 up 2 days, 3:21,  1 user,  load average: 0.15, 0.20, 0.22`

**`uptime -p`**: Prints system uptime in a human-friendly format.
Example: `uptime -p` → `up 2 days, 3 hours, 21 minutes`

**`who`**: Displays which users are currently logged in and their login times.
Useful for checking active sessions on multi-user systems.

**`man <command>`**: Opens the manual for the specified command (e.g., `man uname`).  
**`history`**: Displays a list of recently executed commands.

---

#### **File and Directory Commands:**
7. **`pwd`**: Prints the current working directory.  
8. **`ls`**: Lists files and directories in the current location.  
   - **`ls -a`**: Includes hidden files in the listing.  
   - **`ls <path>`**: Lists files and directories in the specified path (e.g., `ls /etc/`).  
9. **`touch <filename>`**: Creates an empty file with the specified name.

---

#### **Directory Navigation Commands:**
10. **`cd`**: Changes the current directory.  
11. **`cd ..`**: Moves up one directory level.  
12. **`cd <path>`**: Changes to the specified path (e.g., `cd /home/user/`).

---

#### **Privilege Escalation:**
**`sudo su`**: Switches to the root user (requires the user's password for sudo access).

---

#### **Path and Utility Commands:**
14. **`which <command>`**: Displays the path to the binary of a command (e.g., `which ls` shows `/usr/bin/ls`).

---
### **File and Directory Management in Linux**
---

#### **1. Create Files and Directories**
- **`touch <FILE>`**: Creates an empty file with the specified name.  
  Example:  
  ```bash
  touch myfile.txt
  ```
to create multiple file you can use i.e; touch test{1..10}.txt 
  
- **`mkdir <NAME>`**: Creates a new directory with the specified name.  
  Example:  
  ```bash
  mkdir myfolder
  ```

---

#### **2. Copy Files and Directories**
- **Copy File**:  
  ```bash
  cp <FILE> <TARGET>
  ```
  Example:  
  ```bash
  cp myfile.txt /home/user/
  ```

- **Copy Directory (Recursive)**:  
  ```bash
  cp -R <DIR> <TARGET>
  ```
  Example:  
  ```bash
  cp -R myfolder /home/user/
  ```

---

#### **3. Move Files and Directories**
- **Move File**:  
  ```bash
  mv <FILE> <TARGET>
  ```
  Example:  
  ```bash
  mv myfile.txt /home/user/
  ```

- **Move Directory**:  
  ```bash
  mv <DIR> <TARGET>
  ```
  Example:  
  ```bash
  mv myfolder /home/user/
  ```

---

#### **4. Rename Files or Directories**
- **Rename File or Directory**:  
  ```bash
  mv <SOURCE> <NEW_NAME>
  ```
  Example:  
  ```bash
  mv myfile.txt newfile.txt
  mv myfolder newfolder
  ```

---

#### **5. Delete Files and Directories**
- **Delete File**:  
  ```bash
  rm <FILE>
  ```
  Example:  
  ```bash
  rm myfile.txt
  ```

- **Delete Empty Directory**:  
  ```bash
  rmdir <DIR>
  ```
  Example:  
  ```bash
  rmdir myfolder
  ```

- **Delete Non-Empty Directory (Recursive)**:  
  ```bash
  rm -r <DIR>
  ```
  Example:  
  ```bash
  rm -r myfolder
  ```

- **Force Delete (Skip Prompts)**:  
  ```bash
  rm -rf <DIR>
  ```
  Example:  
  ```bash
  rm -rf myfolder
  ```

---

#### **6. Delete All Files in a Directory**
- **Delete Everything Inside a Directory**:  
  ```bash
  rm <DIR>/*
  ```
  Example:  
  ```bash
  rm test/*
  ```

- **Recursive Delete (Including Subdirectories)**:  
  ```bash
  rm -r test
  ```
  Example:  
  ```bash
  rm -r test
  ```

---

### Linux File Viewing and Manipulation Commands:

1. **`cat filename`**  
   - **Purpose**: Displays the entire contents of a file.  
   - **Example**:  
     ```bash
     cat example.txt
     ```

2. **`more filename`**  
   - **Purpose**: Displays file contents page by page, useful for long files.  
   - **Example**:  
     ```bash
     more example.txt
     ```
   - **Navigation**:  
     - Press `Enter` to scroll line by line.  
     - Press `Space` to scroll page by page.

3. **`head /etc/passwd`**  
   - **Purpose**: Displays the first 10 lines of a file by default.  
   - **Example**:  
     ```bash
     head example.txt
     ```

4. **`tail /etc/passwd`**  
   - **Purpose**: Displays the last 10 lines of a file by default.  
   - **Example**:  
     ```bash
     tail example.txt
     ```

5. **`head -n 2 /etc/passwd`**  
   - **Purpose**: Displays the first `n` lines of a file.  
   - **Example**:  
     ```bash
     head -n 5 example.txt  # Displays the top 5 lines
     ```

6. **`tail -n 2 /etc/passwd`**  
   - **Purpose**: Displays the last `n` lines of a file.  
   - **Example**:  
     ```bash
     tail -n 5 example.txt  # Displays the bottom 5 lines
     ```

7. **`pr /etc/passwd`**  
   - **Purpose**: Formats a file for printing.  
   - **Example**:  
     ```bash
     pr example.txt
     ```

8. **`sort /etc/passwd`**  
   - **Purpose**: Sorts file contents in alphabetical order.  
   - **Example**:  
     ```bash
     sort example.txt
     ```
   - **Options**:  
     - `-r`: Reverse order sorting.  
       ```bash
       sort -r example.txt
       ```
---
### **What is `grep` in Linux?**
- `grep` (Global Regular Expression Print) is a powerful command-line tool used for searching text within files.
- It searches files for lines that match a specified pattern and prints them.


### **Examples of `grep`**

1. **Search for a word in a file:**
   ```bash
   grep "word" filename.txt
   ```
   - Searches for "word" in `filename.txt`.

2. **Case-insensitive search:**
   ```bash
   grep -i "word" filename.txt
   ```
   - Matches "word", "Word", or "WORD".

3. **Search for a word in multiple files:**
   ```bash
   grep "word" file1.txt file2.txt
   ```
   - Searches for "word" in both `file1.txt` and `file2.txt`.

4. **Search recursively in directories:**
   ```bash
   grep -r "word" /path/to/directory
   ```
   - Searches for "word" in all files under the specified directory.

5. **Using `grep` with pipes:**
    ```bash
    ps aux | grep "process"
    ```
    - Filters the output of `ps aux` to show lines containing "process".
---
# **VIM EDITOR**
---

### What is Vim Editor?  
Vim (short for **Vi IMproved**) is a powerful, feature-rich text editor designed for efficient text manipulation and editing. It is based on the **vi** editor but includes several enhancements, such as syntax highlighting, undo/redo functionality, and support for plugins. Vim is commonly used in Linux and Unix systems for editing configuration files, programming, and general text editing tasks.  

---
- **vi**: The original editor, simple and lightweight.  
- **vim**: An enhanced version of vi with many additional features for modern users.  

### Vim Text Editor Basics:

#### **Modes in Vim:**
1. **Command Mode**:  
   - Used for navigation, deletion, and other file operations.  
   - Default mode when Vim is opened.
   
2. **Insert Mode**:  
   - Used for entering text into the file.

#### **Switching Between Modes:**
- **Command Mode → Insert Mode**: Press `i`.  
- **Insert Mode → Command Mode**: Press `Esc`.

---

#### **Saving and Exiting:**
- `:wq`  
  - Save changes and quit Vim.  
- `:q!`  
  - Quit Vim without saving changes.

---

#### **Basic Commands:**
- **`o`**: Open a new line below the current line and enter Insert Mode.  
- **`k`**: Move the cursor up one line.  
- **`j`**: Move the cursor down one line.  
- **`X`**: Delete the character before the cursor.

---

#### **Deletion Commands:**
- **`dw`**: Delete from the cursor to the end of the current word.  
- **`db`**: Delete the word before the cursor.  
- **`dd`**: Delete the entire current line.  
- **`d$`**: Delete from the cursor to the end of the line.  
- **`10dd`**: Delete the next 10 lines starting from the current line.

---

#### **Cursor Navigation:**
- **`nG`**: Move the cursor to the specified line number (`n`).  

---

#### **Line Numbering:**
- **`:set number`**: Display line numbers in Vim.  
- **`:set nonumber`**: Remove line numbers.  

---

### Using ZIP Format in Linux

#### Install ZIP and UNZIP tools:
1. **Install `zip`:**  
   ```
   sudo yum install zip -y
   ```
2. **Install `unzip`:**  
   ```
   sudo yum install unzip -y
   ```

#### Zip Commands:

1. **Zip multiple files into an archive:**  
   ```
   zip archive.zip file1.txt file2.txt file3.txt
   ```
   - Creates a `archive.zip` containing `file1.txt`, `file2.txt`, and `file3.txt`.

2. **Zip all files in the current directory:**  
   ```
   zip archive.zip *
   ```
   - Adds all files in the current directory to `archive.zip`.

3. **Zip an entire folder (including its subdirectories):**  
   ```
   zip -r archive.zip mydirectory
   ```
   - Creates a zip file named `archive.zip` containing the folder `mydirectory` and all its contents recursively.

#### Unzip Commands:
1. **Unzip an archive:**  
   ```
   unzip archive.zip
   ```
   - Extracts the contents of `archive.zip` into the current directory.
#### tar.gz Zip Commands:
1. **Create a .tar.gz archive:**  
   ```
   tar -czvf myfile.tar.gz file1 file2 folder1
   ```
  
2. **Unzip a .tzr.gz archive:**  
   ```
   tar -xzvf myfile.tar.gz
   ```
   - Extracts the contents of `myfile.tar.gz` into the current directory.
---

### Understanding `ECHO` command.

1. **Print text to the terminal:**
   ```bash
   echo "Hello, World!"
   ```
   Output:
   ```
   Hello, World!
   ```

2. **Redirect output to a file:**
   ```bash
   echo "This is a test" > file.txt
   ```
   - Writes "This is a test" into `file.txt`.

3. **Append text to a file:**
   ```bash
   echo "Adding another line" >> file.txt
   ```
   - Adds "Adding another line" to `file.txt`.
   
4. **Print a variable value:**
   ```bash
   name="Avinash"
   echo "Hello, $name!"
   ```
   Output:
   ```
   Hello, Avinash!
   ```

---
# ***Package and Process Management**
---
#### **Package Management**
---

### **1. RPM (RedHat Package Manager):**
- **Purpose:** Manages installation, updates, and removal of software packages on RedHat-based systems.
- **Features:**
  - Does not resolve dependencies automatically.
  - Requires downloading and managing dependencies manually.
  
- **Commands:**
  - Install a package:  
    ```bash
    rpm -ivh package.rpm
    ```
  - Update a package:  
    ```bash
    rpm -Uvh package.rpm
    ```
  - Remove a package:  
    ```bash
    rpm -e package_name
    ```

---

### **2. YUM (Yellowdog Updater Modified):**
- **Purpose:** A wrapper around RPM that automatically resolves dependencies and retrieves packages from repositories.

- **Features:**
  - Resolves dependencies.
  - Retrieves packages from local/global repositories.
  - Enables automatic updates.
   
- **Commands:**
  - Update all packages:  
    ```bash
    yum update
    ```
  - Install a package:  
    ```bash
    yum install package_name
    ```
  - Search for a package:  
    ```bash
    yum search keyword
    ```
  - Remove a package:  
    ```bash
    yum remove package_name
    ```

---

### **3. DNF (Dandified YUM):**
- **Purpose:** The modern package manager that replaces `YUM` in newer Linux distributions, including **Amazon Linux 2023**. 

- **Features:**
  - Faster dependency resolution than YUM.
  - Plugin-based architecture.
  - Supports rollback of transactions.
  - Enhanced handling of large data sets.
  - Secure and efficient.
  
- **Commands:**
  - Install a package:  
    ```bash
    dnf install package_name
    ```
  - Update all packages:  
    ```bash
    dnf update
    ```
  - Remove a package:  
    ```bash
    dnf remove package_name
    ```
  - Search for a package:  
    ```bash
    dnf search keyword
    ```
  - View installed packages:  
    ```bash
    dnf list installed
    ```
  - Enable a repository:  
    ```bash
    dnf config-manager --set-enabled repository_name
    ```

---

- **Repository Configuration:**  
  - Files located in `/etc/yum.repos.d/` or `/etc/dnf/dnf.conf` contain information about enabled repositories.

#### **1. Repository Location:**
-  /etc/yum.repos.d/*.repo` Contains `.repo` configuration files.

---

### **Package Installation Examples**

#### **Apache Installation:**
1. Search for Apache:  
   ```bash
   dnf search httpd
   ```
2. Get information about Apache:  
   ```bash
   dnf info httpd
   ```
3. Install Apache:  
   ```bash
   dnf install httpd
   ```
4. Start and enable Apache:  
   ```bash
   systemctl start httpd  (0r) Service httpd start
   systemctl enable httpd (or) chkconfig httpd on
   ```

---

## **Process Management**

### Identifying and Managing Process IDs (PIDs) in Linux

#### **What is a PID?**
- A PID (Process ID) is a unique identifier assigned by the operating system to each running process.

---

#### **Commands to Identify PIDs and Manage Processes**

1. **View Background and Suspended Jobs:**
   - `jobs`: Displays all background and suspended processes in the current shell.

2. **View the Process Tree:**
   - `pstree`: Shows the process tree in a hierarchical structure.
   - `pstree | less`: Use with `less` to view the process tree page by page.

3. **List Running Processes:**
   - `ps`: Displays processes running in the current terminal.
   - `ps aux`: Lists all running processes across the system in a detailed format.
   - `ps faux`: Displays the process tree along with detailed process information.

4. **Real-Time Process Monitoring:**
   - `top`: Displays a continuously updating list of running processes, their CPU, memory usage, etc. Press `z` for a colorized view.

5. **Quit from any Continuous Process View:**
   - Press `q` to exit from commands like `top`.

#### **Killing a Process**
1. **Terminate a Process by PID:**
   - `kill PID`: Terminates the process with the specified PID.

For example:
   ```
   ps aux | grep some-process
   kill 1234  # Replace 1234 with the actual PID of the process.
   ```

---

#### **System and Memory Information**

1. **Check System Uptime:**
   - `uptime`: Provides the time since the system was last booted, along with load averages.

2. **Check Free Memory:**
   - `free`: Displays memory usage statistics.
   - `free -h`: Displays memory usage in a human-readable format.

---
# User Management in linux

---

| **Command**   | **Description**                          | **Example**                                    |
|---------------|------------------------------------------|------------------------------------------------|
| `useradd`     | Create a new user.                      | `sudo useradd avinash`                         |
| `passwd`      | Set or update a user’s password.        | `sudo passwd avinash`                          |
| `usermod`     | Modify an existing user.                | `sudo usermod -aG wheel avinash`               |
| `userdel`     | Delete a user account.                  | `sudo userdel avinash`                         |
| `id`          | Display user and group IDs.             | `id avinash`                                   |
| `groups`      | Show groups a user belongs to.          | `groups avinash`                               |
| `whoami`      | Show the currently logged-in user.      | `whoami`                                       |
| `su`          | Switch to another user.                 | `su - avinash`                                 |
| `sudo`        | Execute commands as another user.       | `sudo yum update`                              |
| `groupadd`    | Create a new group.                     | `sudo groupadd developers`                     |
| `usermod -g`  | Change a user’s primary group.           | `sudo usermod -g developers avinash`           |
| `usermod -G`  | Add a user to a secondary group.         | `sudo usermod -aG wheel avinash`               |
| `gpasswd`     | Add or remove users from a group.        | `sudo gpasswd -a avinash developers`           |
| `deluser`     | Remove a user from a group.              | `sudo gpasswd -d avinash developers`           |

---

### **Important User Management Commands in Linux**

1. **Create a New User**
   - Command:  
     ```bash
     sudo useradd username
     ```
2. **Set a Password for the User**
   - Command:  
     ```bash
     sudo passwd username
     ```
     This sets or updates the password for the user.

3. **Enable Password Authentication**
   - **Step 1:** Edit the SSH configuration file to enable password authentication:  
     ```bash
     sudo vim /etc/ssh/sshd_config
     ```
   - **Step 2:** Locate and update these lines:
     ```plaintext
     PasswordAuthentication yes
     ```
   - **Step 3:** Restart the SSH service to apply changes:
     ```bash
     sudo systemctl restart sshd
     ```

4. **Switch to Another User**
   - Command:  
     ```bash
     su - username
     ```
     This command allows you to log in as another user and access their environment.
To add a user to the `wheel` group, which grants sudo permissions on many Linux distributions, you can use the following command:

```bash
sudo usermod -aG wheel username
```
---

### Verify the User's Group Membership
After adding the user, you can verify their group memberships using:
```bash
groups username
```
---

### **Additional User Management Commands**
- **Delete a User:**  
  ```bash
  sudo userdel username
  ```
  To delete the user along with their home directory:
  ```bash
  sudo userdel -r username
  ```

- **View User Details:**  
  ```bash
  id username
  ```
- **View Currently Logged-in Users:**  
  ```bash
  who
  ```
---

**To log in directly as another user to your EC2 instance without using a keypair, you can set up password-based authentication.
**
---

#### 1. **Switch to the User and Set a Password**
   - Create a new user (if not already created):
     ```bash
     sudo useradd -m username
     ```
   - Set a password for the user:
     ```bash
     sudo passwd username
     ```

#### 2. **Enable Password Authentication for SSH**
   - Edit the SSH configuration file:
     ```bash
     sudo vim /etc/ssh/sshd_config
     ```
   - Look for the following lines and update them:
     ```plaintext
     PasswordAuthentication yes
     ```
   - Save and exit the editor.

#### 3. **Restart the SSH Service**
   - Restart the SSH service to apply changes:
     ```bash
     sudo systemctl restart sshd
     ```
#### 4. **Connect to the EC2 Instance**
   - Use an SSH client to log in with the username and password:
     ```bash
     ssh username@<EC2-Public-IP>
     ```
   - You will be prompted for the password set in Step 1.

---
# File and Directory Permissions Management in Amazon Linux 2023
---

In Amazon Linux 2023, managing file and directory permissions is done using the `chmod`, `chown`, and `chgrp` commands. Below is a table that explains common permission commands using the **numeric method** (also known as octal notation).

---

### Understanding Numeric (Octal) Permissions

- **4** – Read (`r`)  
- **2** – Write (`w`)  
- **1** – Execute (`x`)  

The permissions are set in three levels:
- **User (Owner)**  
- **Group**  
- **Others (World)**  

### Numeric Values:
- `0` – No permission  
- `1` – Execute only  
- `2` – Write only  
- `3` – Write and execute  
- `4` – Read only  
- `5` – Read and execute  
- `6` – Read and write  
- `7` – Read, write, and execute  

---

### Permissions Management Commands Table

| **Command**    | **Description**                            | **Example**                     |
|----------------|--------------------------------------------|---------------------------------|
| `chmod 400`    | Owner: Read only, No access for others.    | `chmod 400 file.txt`            |
| `chmod 600`    | Owner: Read and write, No access for others. | `chmod 600 file.txt`            |
| `chmod 700`    | Owner: Full access, No access for others.  | `chmod 700 script.sh`           |
| `chmod 644`    | Owner: Read and write, Others: Read only.  | `chmod 644 file.txt`            |
| `chmod 664`    | Owner and group: Read and write, Others: Read. | `chmod 664 file.txt`        |
| `chmod 755`    | Owner: Full access, Others: Read and execute. | `chmod 755 script.sh`       |
| `chmod 777`    | Everyone: Full access.                     | `chmod 777 file.txt`            |
| `chmod 000`    | No one has any permission.                 | `chmod 000 file.txt`            |
| `chown`        | Change file owner.                        | `sudo chown avinash file.txt`   |
| `chgrp`        | Change file group.                        | `sudo chgrp developers file.txt` |
| `chown -R`     | Change ownership recursively.              | `sudo chown -R avinash /data`   |
| `chmod -R`     | Change permissions recursively.            | `chmod -R 755 /scripts`         |

---

### Explanation and Example Commands

1. **Set Read-only Permission for Owner**
```bash
chmod 400 file.txt
```
- Owner can read the file, others have no access.

2. **Set Full Permission for Owner, No Access for Others**
```bash
chmod 700 script.sh
```
- Owner has read, write, and execute permissions.

3. **Allow Read and Write for Owner and Group, Read for Others**
```bash
chmod 664 file.txt
```
- Owner and group can read and write, others can only read.

4. **Set Full Access for Everyone**
```bash
chmod 777 file.txt
```
- Everyone has read, write, and execute permissions.

5. **Change File Owner**
```bash
sudo chown avinash file.txt
```
- Changes the owner to `avinash`.

6. **Change File Group**
```bash
sudo chgrp developers file.txt
```
- Changes the group to `developers`.

7. **Recursively Change Ownership of a Directory**
```bash
sudo chown -R avinash /data
```
- Changes ownership of `/data` and all its contents.

8. **Recursively Apply Permissions**
```bash
chmod -R 755 /scripts
```
- Applies `755` permissions to all files and directories inside `/scripts`.

---

### Quick Reference for Common Permissions

| **Octal** | **Permission**      | **Description**                      |
|-----------|---------------------|--------------------------------------|
| `400`     | r--------            | Owner can read, no access to others |
| `600`     | rw-------            | Owner can read and write            |
| `700`     | rwx------            | Owner has full permissions          |
| `644`     | rw-r--r--            | Owner can read/write, others can read |
| `755`     | rwxr-xr-x            | Owner has full, others can read/execute |
| `777`     | rwxrwxrwx            | Full permissions for everyone       |


---

# SCP (Secure Copy) Command Guide

The `scp` command is used to securely transfer files and directories between systems over SSH.

---

## Basic Syntax

```bash
scp [options] source destination
```

---

## Transfer From Local to Remote

```bash
scp file.txt username@remote_ip:/path/to/destination/
```

- **file.txt** – Local file you want to copy
- **username** – Username on the remote server
- **remote_ip** – IP address or hostname of the remote machine
- **/path/to/destination/** – Target directory on the remote machine

**Example:**
```bash
scp myscript.sh ec2-user@192.168.1.10:/home/ec2-user/
```

---

## Transfer From Remote to Local

```bash
scp username@remote_ip:/path/to/file.txt /local/path/
```

**Example:**
```bash
scp ec2-user@192.168.1.10:/var/log/messages /tmp/
```

---

## Copy Directories Recursively

```bash
scp -r foldername username@remote_ip:/path/to/destination/
```

**Example:**
```bash
scp -r projects/ ec2-user@192.168.1.10:/home/ec2-user/
```

---

## Using Identity File (e.g., AWS .pem Key)

```bash
scp -i mykey.pem file.txt ec2-user@ec2-3-91-145-111.compute-1.amazonaws.com:/home/ec2-user/
```

---
# **VOlume Management**
---

## Volumes Management in AWS

### **What is IOPS?**
**IOPS** stands for **Input/Output Operations Per Second**. It is a performance measurement used to describe the speed at which a storage device can read and write data. This metric is particularly important for applications that rely on high-performance storage, such as databases and high-traffic websites.

### **How IOPS is Calculated**
IOPS is calculated based on the following factors:

1. **Block Size:** 
   - The size of the data blocks being read or written.
   - Common block sizes are 4 KB, 8 KB, or larger.

2. **Latency:**
   - The time taken to process a single I/O request. This includes:
     - **Queue latency:** Time spent waiting in the queue.
     - **Disk latency:** Time taken by the storage media to complete the operation.

3. **Throughput:**
   - The rate at which data is transferred, typically measured in MB/s.

### **IOPS Formula**

**IOPS= Throughput×1024 / BlockSize**

- **Throughput** is in MB/s.
- **Block Size** is in KB.

### **Example**
If a storage device has:
- **Throughput:** 128 MB/s
- **Block Size:** 4 KB

The IOPS can be calculated as:

**IOPS= 128 ×1024 / 4 = 32,768IOPS**

---

### Root Volume
- **Contains OS**: Supported types are `gp2`, `gp3`, `io1`, `io2`, and `magnetic`.


#### Storage Types:
1. **General Purpose SSD (gp2, gp3)**
   - **Suitable for**: Most common workloads.
   - **Key Features**:
     - Low latency.
     - Min: 1 GiB, Max: 16 TiB.
     - Max IOPS: 16,000.
     - gp2: 3 IOPS per GiB with a minimum of 100 IOPS.
     - gp3: Allows specifying required IOPS.

2. **Provisioned IOPS SSD (io1, io2)**
   - **Suitable for**: Workloads requiring specific IOPS or exceeding 16,000 IOPS (e.g., I/O-intensive database workloads).
   - **Key Features**:
     - Min: 4 GiB, Max: 16 TiB.
     - Max IOPS: 64,000 (io1, io2).
     - io2 Block Express: Min: 4 GiB, Max: 64 TiB, Supports up to 256,000 IOPS.

3. **HDD**:
   - **Throughput Optimized HDD (st1)**:
     - Suitable for big data, data warehousing, and log processing.
     - Min: 125 GiB, Max: 16 TiB.
     - Max IOPS: 500, Throughput: 500 MB/s.
   - **Cold HDD (sc1)**:
     - Suitable for less frequently accessed data.
     - Lower cost than st1.
     - Min: 125 GiB, Max: 16 TiB.
     - Max IOPS: 250, Throughput: 250 MB/s.

4. **Magnetic (Standard)**:
   - **Suitable for**: Low-cost storage solutions for less frequently accessed data.
   - Min: 1 GiB, Max: 1 TiB.
---
### **AWS EBS Volume Types and Primary Use Cases**

1. **gp2 (General Purpose SSD):**  
   - **Use Case:** Balanced performance for most workloads.  
   - **Example/Industry:** Small databases, development environments (e.g., retail websites).

2. **gp3 (General Purpose SSD):**  
   - **Use Case:** Cost-effective storage with the ability to provision IOPS and throughput separately.  
   - **Example/Industry:** Application servers, virtual desktops (e.g., SaaS platforms).

3. **io1 (Provisioned IOPS SSD):**  
   - **Use Case:** High-performance storage for critical, latency-sensitive applications.  
   - **Example/Industry:** Large databases (e.g., financial transaction systems).

4. **io2 (Provisioned IOPS SSD):**  
   - **Use Case:** Durable, high-performance storage for mission-critical workloads.  
   - **Example/Industry:** ERP systems, OLTP databases (e.g., healthcare or manufacturing).

5. **st1 (Throughput Optimized HDD):**  
   - **Use Case:** Low-cost, high-throughput storage for large, sequential workloads.  
   - **Example/Industry:** Data warehouses, log processing (e.g., analytics firms).

6. **sc1 (Cold HDD):**  
   - **Use Case:** Lowest-cost storage for infrequently accessed data.  
   - **Example/Industry:** Archiving, backups (e.g., media archives for entertainment).  

---

### File Systems
- **Windows**: FAT, FAT32, NTFS, ReFS.
- **Linux**: ext3, ext4, xfs.

### EBS (Elastic Block Storage)
- Block-based storage designed to run OS and applications.
- **Root Volume**: Supports SSD and magnetic.
- **Additional Volume**: Supports SSD, HDD, and magnetic (st1, sc1).

### Free Tier
- 30 GB of `gp2` or standard storage.
- 20% of volume size or 5 GB, whichever is higher.

---

### Making Additional Volumes Available

#### Windows OS
1. **Disk Management** (`diskmgmt.msc`):
   - Choose volume → Make it online → Initialize disk → Create simple volume → Format with NTFS/FAT.

#### Linux OS
1. **Identify New Volume**:
   - `lsblk`: List block-based devices.
   - `df -Th`: List available volumes.
   - Example: `/dev/xvdf` (new volume).

The `lsblk` and `df` commands in Linux provide information about disk and file systems, but they serve different purposes and present the information in distinct ways. 

  - `lsblk` is hardware-focused and shows all block devices, whether mounted or not.
  - `df` is file system-focused and only shows mounted partitions.


| **Command** | **Purpose** | **Output Focus** | **Key Use Cases** |
|-------------|-------------|------------------|-------------------|
| `lsblk`     | Lists information about block devices. | Details about block devices, such as disks and their partitions (e.g., size, type, mount points). | Viewing disk layout, identifying devices, and checking partitions and mount points. |
| `df`        | Displays disk space usage of file systems. | File system storage details (e.g., total size, used, available, and percentage of use). | Monitoring file system usage, checking disk space on mounted file systems. |



2. **Prepare Volume**:
   - Check file system: `file -s /dev/xvdf`.
     - Output “data”: No file system.
     - Output ext3/xfs: File system present.
   - Create file system: `mkfs -t xfs /dev/xvdf`.
   - Create mount point: `mkdir newvolume`.
   - Mount volume: `mount /dev/xvdf newvolume/`.

3. **Make Mount Persistent**:
   - Check current mounts: `cat /etc/mtab`.
   - Example Entry:
     ```
     /dev/xvdf /home/ec2-user/newvolume xfs rw,relatime,attr2,inode64,noquota 0 0
     ```
   - Add entry to `/etc/fstab`:
     ```
     /dev/xvdf /home/ec2-user/newvolume xfs rw,relatime,attr2,inode64,noquota 0 0
     ```
   - Apply changes: `mount -a`.

---

### Increasing Volume Size with Amazon Linux 2
1. Increase the size in the AWS console.
2. Install `xfsprogs`: `yum install xfsprogs`.
3. Expand volume:
   ```
   xfs_growfs -d /volume-Mountpoint
   xfs_growfs -d /home/ec2-user/newvolume
   ```

### Increasing Volume Size with Amazon Linux 2023
1. Increase the size in the AWS console.
2. Install `growpart` (if not available).
3. Expand the partition first:
   ```
   growpart /dev/xvda 1
   xfs_growfs -d /volume-Mountpoint
   xfs_growfs -d /
   ```

**Note**: Decreasing volume size is not supported at movement.
