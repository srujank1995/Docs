Here’s a comprehensive list of Linux commands related to account management, password aging, `su`/`sudo`, and firewall management:

### 1. **Linux Account Management**

#### User Management
- **Add a new user**:  
  ```bash
  sudo useradd <username>
  ```
- **Create a user with a home directory**:  
  ```bash
  sudo useradd -m <username>
  ```
- **Delete a user**:  
  ```bash
  sudo userdel <username>
  ```
- **Delete user along with home directory**:  
  ```bash
  sudo userdel -r <username>
  ```
- **Modify a user**:  
  ```bash
  sudo usermod -<options> <username>
  ```
  (e.g., `-l` for changing username, `-d` for changing home directory, etc.)
  
#### Group Management
- **Create a new group**:  
  ```bash
  sudo groupadd <groupname>
  ```
- **Add user to a group**:  
  ```bash
  sudo usermod -aG <groupname> <username>
  ```
- **List groups for a user**:  
  ```bash
  groups <username>
  ```
- **Delete a group**:  
  ```bash
  sudo groupdel <groupname>
  ```

#### Account Information
- **Display user details**:  
  ```bash
  id <username>
  ```
- **View `/etc/passwd` file (lists all system users)**:  
  ```bash
  cat /etc/passwd
  ```
- **View `/etc/group` file (lists all groups)**:  
  ```bash
  cat /etc/group
  ```
- **View `/etc/shadow` file (password details, root access required)**:  
  ```bash
  sudo cat /etc/shadow
  ```

### 2. **Linux Password Aging Management**

- **Change password aging information**:  
  ```bash
  sudo chage <options> <username>
  ```
  Options:
  - `-l`: Display aging information.
  - `-m`: Minimum number of days between password changes.
  - `-M`: Maximum number of days the password is valid.
  - `-W`: Number of days of warning before password expiration.
  - `-I`: Number of inactive days after password expires before locking.

- **Example** (Set password to expire every 90 days with a 7-day warning):
  ```bash
  sudo chage -M 90 -W 7 <username>
  ```

- **Force a user to change password at next login**:  
  ```bash
  sudo chage -d 0 <username>
  ```

- **Lock a user account**:  
  ```bash
  sudo usermod -L <username>
  ```
- **Unlock a user account**:  
  ```bash
  sudo usermod -U <username>
  ```

### 3. **Linux `su` and `sudo` Commands**

#### `su` (Switch User)
- **Switch to root user**:  
  ```bash
  su -
  ```
- **Switch to a different user**:  
  ```bash
  su <username>
  ```
- **Exit from `su` session**:  
  ```bash
  exit
  ```

#### `sudo` (Superuser Do)
- **Run a command as root**:  
  ```bash
  sudo <command>
  ```
- **Execute a command as another user**:  
  ```bash
  sudo -u <username> <command>
  ```
- **View sudoers file**:  
  ```bash
  sudo visudo
  ```
  (This is used to manage who can run `sudo` commands and under what conditions.)

- **Add a user to the sudo group** (allowing them to run sudo commands):  
  ```bash
  sudo usermod -aG sudo <username>
  ```

- **Run a command without needing a password (edit `/etc/sudoers` file)**:
  ```bash
  <username> ALL=(ALL) NOPASSWD: ALL
  ```

### 4. **Linux Firewall Management (`iptables` and `firewalld`)**

#### **Using `iptables`**:
- **Check existing firewall rules**:  
  ```bash
  sudo iptables -L
  ```
- **Allow incoming SSH connection**:  
  ```bash
  sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
  ```
- **Block all incoming traffic except SSH**:  
  ```bash
  sudo iptables -P INPUT DROP
  sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
  sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
  ```
- **Save iptables rules** (so they persist across reboots):
  - On Debian-based systems:
    ```bash
    sudo sh -c "iptables-save > /etc/iptables/rules.v4"
    ```
  - On Red Hat-based systems:
    ```bash
    sudo service iptables save
    ```

#### **Using `firewalld`**:
- **Check firewall status**:  
  ```bash
  sudo firewall-cmd --state
  ```
- **Start and enable `firewalld`**:  
  ```bash
  sudo systemctl start firewalld
  sudo systemctl enable firewalld
  ```
- **Allow a service (e.g., SSH)**:  
  ```bash
  sudo firewall-cmd --permanent --add-service=ssh
  sudo firewall-cmd --reload
  ```
- **Block a service**:  
  ```bash
  sudo firewall-cmd --permanent --remove-service=<service>
  sudo firewall-cmd --reload
  ```
- **List active zones**:  
  ```bash
  sudo firewall-cmd --get-active-zones
  ```
- **Add a port to the firewall**:  
  ```bash
  sudo firewall-cmd --permanent --add-port=8080/tcp
  sudo firewall-cmd --reload
  ```
- **List all firewall rules**:  
  ```bash
  sudo firewall-cmd --list-all
  ```

These commands should help you manage user accounts, password policies, `su`/`sudo` commands, and firewalls on Linux systems.
