# Windows Commands

This documentation covers useful Windows commands for managing the system, file operations, networking, process management, and more.

---

## System Information

### 1. **System Info**
   - `systeminfo`  
     Display detailed system configuration and information.
   - `hostname`  
     Display the system's hostname.
   - `ver`  
     Display the version of Windows running on the system.
   - `wmic os get caption`  
     Display the operating system name.
   - `wmic cpu get caption`  
     Display CPU information.
   - `wmic memorychip get capacity`  
     Show the memory capacity in the system.

### 2. **CPU and Memory Usage**
   - `tasklist`  
     List all running processes.
   - `tasklist /fi "imagename eq <processname>"`  
     Filter processes by name.
   - `taskkill /im <processname> /f`  
     Forcefully terminate a process.
   - `wmic process list brief`  
     List processes with brief details.
   - `get-process`  
     Show a list of all active processes (PowerShell).

### 3. **Disk Usage**
   - `wmic logicaldisk get size,freespace,caption`  
     Display disk space information for all drives.
   - `dir`  
     List files and directories in the current directory.
   - `chkdsk`  
     Check a disk for errors.

### 4. **Network Info**
   - `ipconfig`  
     Display IP configuration and network adapter information.
   - `ipconfig /all`  
     Show detailed IP configuration.
   - `ipconfig /flushdns`  
     Clear the DNS resolver cache.
   - `ping <hostname/ip>`  
     Check the network connection to a host.
   - `tracert <hostname/ip>`  
     Trace the path packets take to reach a host.
   - `netstat`  
     Display active connections and listening ports.
   - `netsh interface ip show config`  
     Show network interface configuration.

---

## File Operations

### 1. **File Management**
   - `dir`  
     List the contents of a directory.
   - `cd <path>`  
     Change the current directory.
   - `cd ..`  
     Go up one level in the directory.
   - `mkdir <foldername>`  
     Create a new folder.
   - `rmdir <foldername>`  
     Remove a folder.
   - `del <filename>`  
     Delete a file.
   - `del /f /q <filename>`  
     Force delete a file without confirmation.
   - `copy <source> <destination>`  
     Copy a file from source to destination.
   - `move <source> <destination>`  
     Move a file or folder.
   - `rename <oldname> <newname>`  
     Rename a file or folder.
   - `xcopy <source> <destination>`  
     Copy files and directories, including subdirectories.

### 2. **File Permissions**
   - `icacls <file>`  
     Show file or directory permissions.
   - `icacls <file> /grant <username>:(F)`  
     Grant full control permissions to a user.
   - `icacls <file> /deny <username>:(F)`  
     Deny full control permissions to a user.

### 3. **Search Commands**
   - `dir /s /b <searchterm>`  
     Search for a file within a directory and its subdirectories.
   - `findstr <searchterm> <filename>`  
     Search for a string in a file.

---

## User and Group Management

### 1. **User Management**
   - `net user`  
     Display all user accounts on the system.
   - `net user <username> <password> /add`  
     Create a new user with a password.
   - `net user <username> /delete`  
     Delete a user account.
   - `net localgroup <groupname> <username> /add`  
     Add a user to a group.
   - `net localgroup <groupname> <username> /delete`  
     Remove a user from a group.
   - `net user <username> <password>`  
     Change a user's password.

### 2. **Group Management**
   - `net localgroup`  
     List all local groups.
   - `net localgroup <groupname> /add`  
     Create a new group.
   - `net localgroup <groupname> /delete`  
     Delete a group.

---

## Process Management

### 1. **Task Management**
   - `tasklist`  
     Display all running processes.
   - `taskkill /f /im <processname>`  
     Kill a running process by its name.
   - `taskkill /f /pid <PID>`  
     Kill a process by its Process ID (PID).

### 2. **Windows Services**
   - `net start`  
     List all running services.
   - `net stop <service>`  
     Stop a service.
   - `net start <service>`  
     Start a service.
   - `sc query`  
     Query service status.

---

## Networking

### 1. **Network Commands**
   - `ping <hostname>`  
     Send an ICMP echo request to a remote host.
   - `tracert <hostname>`  
     Trace the route packets take to a host.
   - `netstat`  
     Show active network connections.
   - `netstat -an`  
     Show all active connections and listening ports.
   - `nslookup <hostname>`  
     Query DNS to resolve a hostname to an IP address.

### 2. **Network Configuration**
   - `ipconfig`  
     Display basic IP configuration.
   - `ipconfig /release`  
     Release the current IP address.
   - `ipconfig /renew`  
     Renew the IP address.
   - `netsh wlan show profiles`  
     Show all saved Wi-Fi profiles.
   - `netsh wlan connect name=<profile>`  
     Connect to a Wi-Fi network using a saved profile.

---

## Disk and Storage Management

### 1. **Disk Management**
   - `diskpart`  
     Open the disk partition tool.
   - `diskpart list disk`  
     List all disks.
   - `diskpart select disk <disknumber>`  
     Select a specific disk.
   - `diskpart clean`  
     Clean a selected disk (remove all partitions).
   - `chkdsk <driveletter>: /f`  
     Check and repair the file system on a drive.

---

## System Performance

### 1. **Monitor System Resources**
   - `taskmgr`  
     Open Task Manager.
   - `perfmon`  
     Open Performance Monitor.
   - `resmon`  
     Open Resource Monitor.
   - `systeminfo`  
     Display system information, including uptime.

### 2. **Clear Temp Files**
   - `del /f /q %temp%\*`  
     Delete all files in the Temp directory.

---

## Shutdown and Reboot

### 1. **Shutdown and Reboot**
   - `shutdown /s /f /t 0`  
     Shutdown the computer immediately.
   - `shutdown /r /f /t 0`  
     Restart the computer immediately.
   - `shutdown /l`  
     Log off the current user.
   - `shutdown /a`  
     Abort a system shutdown (if timed shutdown is in progress).

---

## Windows PowerShell Commands

### 1. **PowerShell Basics**
   - `Get-Process`  
     List all running processes (PowerShell equivalent of `tasklist`).
   - `Stop-Process -Name <processname>`  
     Kill a process by name.
   - `Start-Service <service>`  
     Start a service.
   - `Stop-Service <service>`  
     Stop a service.
   - `Get-Service`  
     List all services and their statuses.
   - `Set-ExecutionPolicy RemoteSigned`  
     Change the script execution policy to allow local scripts to run.

---

## Conclusion

This documentation essential Windows commands for managing files, networking, processes, services, and more. Keep this as a quick reference for day-to-day tasks and troubleshooting.

