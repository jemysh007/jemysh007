# Ubuntu Commands

This cheat sheet covers a range of useful and powerful Ubuntu commands. From system information to performance stats, file operations, networking, and package management, this is a one-stop guide to essential Ubuntu commands.

---

## System Information

### 1. **System Info**
   - `uname -a`  
     Display all system information.
   - `hostname`  
     Show system's hostname.
   - `lsb_release -a`  
     Display Linux distribution information.
   - `cat /etc/os-release`  
     Show distribution details.
   - `uptime`  
     Display system uptime.
   - `arch`  
     Show system architecture (x86_64, etc.).

### 2. **Memory Usage**
   - `free -h`  
     Show memory and swap usage in a human-readable format.
   - `vmstat`  
     Display memory, paging, block IO, and CPU statistics.
   - `top`  
     Monitor system resources and processes in real-time.
   - `htop`  
     An interactive process viewer (more advanced than `top`).
   - `cat /proc/meminfo`  
     Detailed memory usage from `/proc`.

### 3. **CPU Info**
   - `lscpu`  
     Display CPU architecture information.
   - `cat /proc/cpuinfo`  
     Show detailed CPU information.
   - `mpstat`  
     Report CPU statistics.
   - `watch -n 1 "cat /proc/cpuinfo"`  
     Monitor CPU usage dynamically.

### 4. **Disk Usage**
   - `df -h`  
     Show disk space usage in a human-readable format.
   - `du -sh *`  
     Display the size of files/folders in the current directory.
   - `lsblk`  
     List all block devices (disks, partitions).
   - `fdisk -l`  
     List disk partitions and file system types.
   - `iostat`  
     Show input/output stats for devices.

### 5. **Network Info**
   - `ifconfig`  
     Show all network interfaces and their statuses.
   - `ip a`  
     Display detailed network interface info (alternative to `ifconfig`).
   - `ip link show`  
     Show network interfaces with their states.
   - `ss -tuln`  
     Show active listening sockets.
   - `netstat -tuln`  
     Display active network connections.
   - `ping <hostname/ip>`  
     Check connectivity to a remote host.
   - `traceroute <hostname/ip>`  
     Trace the path to a remote host.
   - `dig <domain>`  
     DNS lookup.

### 6. **Process Info**
   - `ps aux`  
     List all running processes.
   - `top`  
     Real-time process monitoring.
   - `htop`  
     Interactive and more user-friendly version of `top`.
   - `kill <pid>`  
     Terminate a process by its PID.
   - `killall <process-name>`  
     Kill all instances of a given process.

---

## File System Operations

### 1. **File Management**
   - `ls`  
     List directory contents.
   - `cd <dir>`  
     Change to a specified directory.
   - `pwd`  
     Print the current working directory.
   - `cp <source> <destination>`  
     Copy files or directories.
   - `mv <source> <destination>`  
     Move or rename files.
   - `rm <file>`  
     Remove a file.
   - `rm -rf <dir>`  
     Recursively remove a directory.
   - `find <dir> -name <pattern>`  
     Find files by name within a directory.
   - `locate <file>`  
     Locate a file using the database (requires `updatedb`).
   - `ln -s <target> <link>`  
     Create a symbolic link (symlink) to a file or directory.  
     Example: `ln -s /path/to/original /path/to/symlink`

### 2. **File Permissions**
   - `chmod 755 <file>`  
     Change file permissions (read, write, execute).
   - `chown <user>:<group> <file>`  
     Change file owner and group.
   - `ls -l`  
     List files with detailed permissions.
   - `umask`  
     Show the current file creation mask.

### 3. **Disk Operations**
   - `mount <device> <mount-point>`  
     Mount a filesystem.
   - `umount <device>`  
     Unmount a filesystem.
   - `fsck <device>`  
     Check and repair a filesystem.
   - `tune2fs -l <device>`  
     Display filesystem info for ext-based systems.

### 4. **Archive & Compression**
   - `tar -czvf archive.tar.gz <files>`  
     Create a compressed tarball.
   - `tar -xzvf archive.tar.gz`  
     Extract a tarball.
   - `zip archive.zip <files>`  
     Create a zip archive.
   - `unzip archive.zip`  
     Extract a zip archive.
   - `gzip <file>`  
     Compress a file using gzip.
   - `gunzip <file.gz>`  
     Decompress a gzipped file.

---

## Package Management

### 1. **APT Commands (Debian/Ubuntu)**
   - `sudo apt update`  
     Update package index.
   - `sudo apt upgrade`  
     Upgrade installed packages.
   - `sudo apt install <package>`  
     Install a package.
   - `sudo apt remove <package>`  
     Remove a package.
   - `sudo apt purge <package>`  
     Completely remove a package (including configuration files).
   - `sudo apt autoremove`  
     Remove unused packages.
   - `apt-cache search <package>`  
     Search for a package.
   - `apt show <package>`  
     Show details about a package.

### 2. **Snap Commands**
   - `sudo snap install <package>`  
     Install a snap package.
   - `sudo snap remove <package>`  
     Remove a snap package.
   - `snap list`  
     List installed snap packages.

### 3. **Flatpak Commands**
   - `flatpak install <package>`  
     Install a Flatpak package.
   - `flatpak uninstall <package>`  
     Remove a Flatpak package.
   - `flatpak list`  
     List installed Flatpak packages.

---

## User and Group Management

### 1. **User Management**
   - `sudo adduser <username>`  
     Create a new user.
   - `sudo deluser <username>`  
     Delete a user.
   - `sudo usermod -aG <group> <username>`  
     Add a user to a group.
   - `sudo passwd <username>`  
     Change user password.
   - `id <username>`  
     Display user information (UID, GID, groups).

### 2. **Group Management**
   - `sudo addgroup <group>`  
     Create a new group.
   - `sudo delgroup <group>`  
     Delete a group.

---

## System Performance

### 1. **Monitor System Load**
   - `uptime`  
     Display system load averages.
   - `top`  
     View real-time system resource usage.
   - `htop`  
     Interactive process viewer (with more features).
   - `glances`  
     Real-time system monitoring tool (requires installation).

### 2. **Disk I/O Monitoring**
   - `iotop`  
     Show real-time disk I/O usage (requires root).
   - `dstat`  
     Display resource statistics (disk, CPU, network).

---

## Networking

### 1. **Check Network Connections**
   - `ping <host>`  
     Ping a host to check connectivity.
   - `traceroute <host>`  
     Trace the route packets take to a host.
   - `curl <url>`  
     Transfer data from or to a server.
   - `wget <url>`  
     Download files from a URL.

### 2. **Network Config**
   - `ip addr`  
     Show IP address and interface details.
   - `ifconfig`  
     Display network interfaces.
   - `nmcli`  
     NetworkManager command-line interface.
   - `netstat`  
     Show network connections and statistics.
   - `ss`  
     Show socket statistics.

---

## Logs and Monitoring

### 1. **System Logs**
   - `journalctl`  
     View system logs.
   - `dmesg`  
     Show boot and system messages.
   - `tail -f /var/log/syslog`  
     View system logs in real-time.
   - `cat /var/log/auth.log`  
     View authentication logs.

### 2. **Log Rotation**
   - `logrotate`  
     Manage log file rotation.

---

## Other Useful Commands

### 1. **Search Commands**
   - `grep <pattern> <file>`  
     Search for a pattern in a file.
   - `find /path -name <pattern>`  
     Find files by name in a directory.
   - `locate <filename>`  
     Locate a file by its name (requires `updatedb`).

### 2. **System Shutdown and Reboot**
   - `sudo shutdown -h now`  
     Shutdown the system immediately.
   - `sudo reboot`  
     Reboot the system.

---

## Magic Commands

### 1. **`!!`**
   - Run the last command again.

### 2. **`history`**
   - Show command history.


   
### 3. **`sudo !!`**
   - Run the last command with `sudo`.

### 4. **`!<string>`**
   - Run the last command that starts with `<string>`.

### 5. **`ctrl + r`**
   - Reverse search in command history.

---

## Conclusion

This cheat sheet covers a wide variety of Ubuntu commands. Use these to quickly perform common tasks, troubleshoot issues, and monitor system performance. Happy working with Ubuntu!
