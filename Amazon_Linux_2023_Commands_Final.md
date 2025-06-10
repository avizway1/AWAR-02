
# Linux Essentials and Advanced Commands Guide (Amazon Linux 2023 Focus)

This guide is a fully rebuilt and structured document based on your original content. It retains all your original commands, adds precise Amazon Linux 2023 notes, and expands with explanations wherever needed.

---

## 🔧 Basic System Commands (Amazon Linux 2023)

```bash
whoami          # Display the current user
hostname        # Print or set the hostname
date            # Show the current system date and time
uptime          # System uptime and load average
clear           # Clear terminal screen
history         # View the command history
```

Use `!!` to re-run the last command, or `!<command>` to repeat a previous one, e.g., `!ls`.

```bash
CTRL + R        # Interactive search through history
alias l='ls -lah'  # Create a shortcut alias for listing
```

---

## 📁 File and Directory Operations

```bash
pwd                    # Show the current directory
ls -la                 # List all files including hidden
ls -a /etc             # List contents of specific directory
touch myfile.txt       # Create an empty file
mkdir myfolder         # Create a new directory
rm -rf myfolder        # Remove directory and its contents
cp file.txt /tmp/      # Copy file to another location
cp -R dir /target/     # Recursively copy directory
mv old new             # Rename or move file/directory
```

---

## 🧰 File Permissions and Ownership

Octal permission reference: 7 (rwx), 6 (rw-), 5 (r-x), 4 (r--), etc.

```bash
chmod 755 file.sh         # rwxr-xr-x
chmod 644 file.txt        # rw-r--r--
chmod -R 700 scripts/     # Recursive full permission to owner
chown ec2-user file.txt   # Change file owner
chgrp dev file.txt        # Change group
```

---

## 📦 Package Management (Amazon Linux 2023 uses dnf)

```bash
dnf update                      # Update all packages
dnf install nginx               # Install nginx web server
dnf remove nginx                # Remove installed package
dnf list installed              # List all installed packages
dnf search git                  # Search for packages with 'git'
dnf info httpd                  # Show detailed info about httpd
dnf config-manager --set-enabled extras  # Enable optional repo
```

---

## 📂 File Viewing and Manipulation

```bash
cat file.txt                   # Display file content
less file.txt                  # Scrollable file viewer
more file.txt                  # Page-wise viewer
head -n 5 file.txt             # First 5 lines
tail -n 10 file.txt            # Last 10 lines
wc -l file.txt                 # Line count
sort file.txt                  # Sort alphabetically
sort -r file.txt               # Reverse sort
pr file.txt                    # Format file for printing
```

---

## 🔍 Search and Filters

```bash
grep 'pattern' file.txt           # Search for pattern
grep -i 'pattern' file.txt        # Case-insensitive search
grep -r 'pattern' /path           # Recursive directory search
ps aux | grep httpd               # Filter processes
find /var -name '*.log'           # Find log files
find . -type f -mtime -1          # Files modified in the last 1 day
xargs rm < files.txt              # Delete files from list
```

---

## 🌐 Networking (Amazon Linux 2023)

```bash
ip a                           # Display IP addresses
ss -tuln                       # Show open TCP/UDP ports
ping -c 3 google.com           # Test internet
traceroute amazon.com          # Trace route to host (dnf install traceroute)
dig amazon.com +short          # Get DNS info (dnf install bind-utils)
curl -I https://example.com    # Fetch HTTP headers
```

---

## 🖥️ System and Performance Monitoring

```bash
top                              # Real-time processes
htop                             # Enhanced viewer (dnf install htop)
ps aux                           # List all running processes
vmstat 1                         # CPU/memory stats
free -h                          # Human-readable memory usage
iostat -xz 1                     # Disk stats (dnf install sysstat)
uptime -p                        # Pretty uptime
watch -n 1 df -h                 # Live disk usage
```

---

## 🔐 User and Group Management

```bash
sudo useradd avinash             # Create new user
sudo passwd avinash              # Set password
sudo userdel -r avinash          # Delete user and home
sudo usermod -aG wheel avinash   # Add to sudo group
id avinash                       # Show user UID/GID
groups avinash                   # Show group membership
su - avinash                     # Switch to user
```

Enable password login for SSH:
```bash
sudo vim /etc/ssh/sshd_config
# Change or add: PasswordAuthentication yes
sudo systemctl restart sshd
```

---

## 🔁 Scheduling with Crontab

```bash
crontab -e                          # Edit current user cron jobs
@reboot /home/ec2-user/init.sh     # Run script at boot
0 3 * * * /backup.sh               # Run daily at 3AM
```

---

## 📄 Archiving and Compression

```bash
tar -czvf archive.tar.gz dir/      # Create .tar.gz
zip -r archive.zip dir/            # Create zip (dnf install zip)
unzip archive.zip                  # Extract zip (dnf install unzip)
tar -xzvf archive.tar.gz           # Extract .tar.gz
gzip file.txt                      # Compress single file
gunzip file.txt.gz                 # Decompress
```

---

## 📜 Vim Editor Essentials

```bash
vim file.txt         # Open file
# Inside Vim:
i       # Enter insert mode
Esc     # Return to command mode
:wq     # Save and exit
:q!     # Quit without saving
:set number      # Show line numbers
:set nonumber    # Hide line numbers
dd, yy, p        # Delete, copy, paste
10dd             # Delete next 10 lines
dw, db, d$       # Delete word/backword/to end of line
```

---

## 🔒 SELinux & Firewall (Amazon Linux 2023)

```bash
getenforce                            # Show SELinux status
setenforce 0                          # Set to permissive

firewall-cmd --state                  # Firewall status
firewall-cmd --list-all               # Show all rules
firewall-cmd --add-port=8080/tcp --permanent
firewall-cmd --reload                 # Apply changes
```

---

## 💾 Disk and Filesystem Management

```bash
lsblk                                 # List block devices
df -Th                                # Filesystem usage with type
du -sh /home/ec2-user                 # Directory size
file -s /dev/xvdf                     # Check if formatted
mkfs -t xfs /dev/xvdf                 # Create XFS filesystem
mkdir /mnt/data                       # Mount point
mount /dev/xvdf /mnt/data             # Mount volume
umount /mnt/data                      # Unmount volume
```
Make it persist after reboot:
```bash
echo "/dev/xvdf /mnt/data xfs defaults 0 0" >> /etc/fstab
mount -a                              # Apply all mounts
```
Resize volume on Amazon Linux 2023:
```bash
sudo growpart /dev/xvda 1             # Expand partition (dnf install cloud-utils-growpart)
xfs_growfs -d /                       # Expand root filesystem
```

---

This updated guide matches the latest Amazon Linux 2023 conventions and best practices for cloud engineers, DevOps teams, and system administrators managing EC2 instances and local resources efficiently.
