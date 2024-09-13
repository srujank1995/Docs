
# Linux Administration Commands and Key Topics for a Linux Administrator (3 Years of Experience)

## 1. System Management

### Check System Information
```bash
uname -a           # Display all system information
hostnamectl        # Show or set the system's hostname and related settings
lsb_release -a     # Display distribution-specific information
```

### Manage System Users and Groups
```bash
adduser USERNAME            # Add a new user
usermod -aG GROUP USERNAME  # Add an existing user to a group
passwd USERNAME             # Change a user's password
groupadd GROUPNAME          # Create a new group
```

### File and Directory Management
```bash
ls -la                       # List files in a directory with detailed information
cp SOURCE DESTINATION        # Copy files or directories
mv SOURCE DESTINATION        # Move or rename files or directories
rm -rf DIRECTORY             # Remove files or directories recursively
chmod PERMISSIONS FILE       # Change file permissions
chown USER:GROUP FILE        # Change file owner and group
```

### Process Management
```bash
ps aux                       # Display all running processes
top                          # Display real-time system processes
htop                         # Interactive process viewer (requires installation)
kill -9 PID                  # Forcefully terminate a process by its PID
systemctl status SERVICE     # Check the status of a service
systemctl restart SERVICE    # Restart a service
```

### Disk Management
```bash
df -h                        # Display disk space usage in human-readable format
du -sh DIRECTORY             # Display the size of a directory
fdisk -l                     # List all disk partitions
mount /dev/sdX /mnt          # Mount a filesystem
umount /mnt                  # Unmount a filesystem
```

### Package Management

#### Debian/Ubuntu
```bash
apt-get update               # Update the package lists
apt-get upgrade              # Upgrade all installed packages
apt-get install PACKAGE      # Install a new package
apt-get remove PACKAGE       # Remove an installed package
```

#### Red Hat/CentOS
```bash
yum update                   # Update the package lists
yum upgrade                  # Upgrade all installed packages
yum install PACKAGE          # Install a new package
yum remove PACKAGE           # Remove an installed package
```

### Network Management
```bash
ip addr show                 # Display network interfaces and IP addresses
ifconfig -a                  # Show all network interfaces
ip link set INTERFACE up     # Bring a network interface up
ip link set INTERFACE down   # Bring a network interface down
ping HOSTNAME_OR_IP          # Send ICMP ECHO_REQUEST to network hosts
netstat -tuln                # Display listening ports and services
traceroute HOSTNAME_OR_IP    # Trace the route packets take to a network host
```

### Firewall Management

#### UFW (Uncomplicated Firewall) - Ubuntu
```bash
ufw status                   # Check the status of the firewall
ufw enable                   # Enable the firewall
ufw disable                  # Disable the firewall
ufw allow PORT               # Allow traffic on a specific port
ufw deny PORT                # Deny traffic on a specific port
```

#### firewalld - CentOS/RedHat
```bash
firewall-cmd --state                         # Check the status of firewalld
firewall-cmd --permanent --add-port=PORT/tcp # Allow traffic on a specific port
firewall-cmd --reload                        # Reload the firewall rules
```

### SSH Management
```bash
ssh user@remote_host                     # Connect to a remote host via SSH
ssh-keygen                               # Generate a new SSH key pair
ssh-copy-id user@remote_host             # Copy SSH key to a remote host for passwordless login
```

## 2. Security

### File and Directory Permissions
```bash
chmod PERMISSIONS FILE               # Change file permissions (e.g., chmod 755 file)
chown USER:GROUP FILE                # Change file owner and group (e.g., chown root:root file)
umask 022                            # Set default file creation permissions
```

### User and Group Security
```bash
passwd USERNAME                      # Set or change a user's password
chage -l USERNAME                    # Display password aging information
usermod -aG sudo USERNAME            # Add a user to the sudoers group (Debian/Ubuntu)
```

### Sudo Configuration
```bash
visudo                               # Edit the sudoers file safely
```

### SELinux (Security-Enhanced Linux)
```bash
getenforce                           # Check SELinux status
setenforce 0                         # Set SELinux to permissive mode
setenforce 1                         # Set SELinux to enforcing mode
sestatus                             # Display the status of SELinux
```

## 3. Backup and Restore

### Creating Backups with tar
```bash
tar cvf backup.tar /path/to/directory   # Create a tar archive of a directory
tar czvf backup.tar.gz /path/to/directory  # Create a compressed tar.gz archive
```

### Restoring from Backups with tar
```bash
tar xvf backup.tar                      # Extract a tar archive
tar xzvf backup.tar.gz                  # Extract a compressed tar.gz archive
```

### rsync for Synchronization and Backup
```bash
rsync -avz /source/path /destination/path   # Synchronize files between directories
rsync -avz user@remote:/source/path /destination/path  # Synchronize files from a remote host
```

## 4. Monitoring and Performance Tuning

### Monitoring System Performance
```bash
top                          # Display real-time system performance
htop                         # Enhanced version of top (requires installation)
iostat                       # Report CPU and I/O statistics
vmstat                       # Report virtual memory statistics
```

### Analyzing System Logs
```bash
tail -f /var/log/syslog                 # View real-time system log updates (Debian/Ubuntu)
tail -f /var/log/messages               # View real-time system log updates (CentOS/RedHat)
journalctl -xe                          # View detailed systemd service logs
```

### Performance Tuning
- **Swappiness**: Adjust how aggressively the kernel swaps memory pages.
  ```bash
  sysctl vm.swappiness=10                # Set swappiness to 10 (less swap usage)
  ```
- **I/O Scheduler**: Choose an appropriate I/O scheduler for your workload.
  ```bash
  echo deadline > /sys/block/sda/queue/scheduler   # Set the I/O scheduler to 'deadline'
  ```

## 5. Automation and Scripting

### Writing and Executing Shell Scripts
- **Create a script**:
  ```bash
  nano script.sh                     # Create a new script using nano editor
  ```
- **Make the script executable**:
  ```bash
  chmod +x script.sh                 # Make the script executable
  ```
- **Run the script**:
  ```bash
  ./script.sh                        # Execute the script
  ```

### Scheduling Jobs with cron
```bash
crontab -e                           # Edit the crontab file to schedule jobs
```
- **Example cron job**: Run a backup script every day at 2 AM.
  ```bash
  0 2 * * * /path/to/backup_script.sh
  ```

## 6. Key Concepts to Understand

1. **File Permissions and Ownership**: Understand how Linux file permissions and ownership work (rwx, chown, chmod).
2. **System Boot Process**: Familiarize yourself with the Linux boot process, including BIOS/UEFI, bootloader (GRUB), and system initialization.
3. **Disk Partitioning and Filesystems**: Know how to partition disks, format filesystems (ext4, xfs), and manage mounts.
4. **Networking Fundamentals**: Understand basic networking concepts, IP addressing, subnetting, and troubleshooting tools (ping, traceroute, netstat).
5. **Firewall Configuration**: Be familiar with setting up and managing firewalls (iptables, ufw, firewalld).
6. **User and Group Management**: Manage users, groups, and permissions to control access to the system.
7. **System Monitoring and Troubleshooting**: Use tools like top, htop, vmstat, iostat, and system logs to monitor and troubleshoot system performance.
8. **Backup and Recovery**: Understand best practices for data backup, recovery, and disaster recovery planning.
9. **Automation and Scripting**: Write and automate tasks using shell scripts, and schedule them with cron jobs.
10. **Security Best Practices**: Implement security best practices, including SSH key management, sudo configuration, SELinux, and user account security.
