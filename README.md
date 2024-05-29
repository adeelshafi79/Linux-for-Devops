# Linux-for-Devops

This repository aims to provide a comprehensive understanding of Linux commands essential for DevOps and Cloud Infrastructure services.

## File and Directory Operations Commands

- **`ls`**: Lists files and directories.
- **`ls -l`**: Displays detailed information about files and directories.
- **`ls -a`**: Shows all files and directories, including hidden files.
- **`ls -h`**: Displays file sizes in a human-readable format.
- **`cd`**: Changes directory.
- **`pwd`**: Displays the current working directory.
- **`mkdir`**: Creates a new directory.
- **`rmdir`**: Removes a directory.
- **`rm`**: Removes files.
- **`cp`**: Copies files and directories.
- **`mv`**: Moves or renames files and directories.
- **`touch`**: Creates an empty file or updates file timestamps.
- **`cat`**: Views the content of a file.
- **`cat > file_name`**: Appends and overwrites text into a file (use CTRL+D to exit).
- **`cat >> file_name`**: Appends without overwriting text into a file (use CTRL+D to exit).
- **`cat f1 f2 > f3`**: Concatenates texts of files f1 and f2 into a new file f3.
- **`head`**: Displays the first few lines of a file.
- **`head -n 5 file_name`**: Displays the first five lines of the file.
- **`tail`**: Displays the last few lines of a file.
- **`tail -n 5 file_name`**: Displays the last five lines of the file.
- **`find`**: Searches for files by name (-name) or by type (-type).
- **`hostname`**: Displays the machine name.
- **`hostname -i`**: Displays the private IP address.
- **`cat /etc/os-release`**: Displays OS version and details.
- **`whoami`**: Displays the current user.

## File Permission Commands

- **`chmod`**: Changes the access modes of a file.
- **`chown`**: Changes the owner of the file or directory.
- **`chgrp`**: Changes the group of a file or directory.
### Access Modes Table

| Access Mode | File status       | Directory status      |
| ----------- | ----------------- | --------------------- |
| r=4         | Display content   | List the content      |
| w=2         | Modify            | Create or remove      |
| x=1         | Execute           | Enter into directory  |

### Permission Symbols Table

| Symbol | Permission                                                 |
| ------ | ---------------------------------------------------------- |
| -      | Regular file                                               |
| d      | Directory                                                  |
| rxw    | Owner: read, write, execute <br> Group: - <br> Others: -  |
| r-x    | Owner: read <br> Group: execute <br> Others: read          |
| r--    | Owner: read <br> Group: - <br> Others: -                  |
| 1      | Symbolic link (hard/soft)                                 |

#### Example

```sh
azureuser@titan3:~/linux-commands/Linux-for-Devops$ ls -l
total 8
-rw-rw-r-- 1 azureuser azureuser 183 May 27 09:56 README.md
drwxrwxr-x 2 azureuser azureuser 4096 May 27 12:35 next
```

The number shown after "total" is the sum of the block counts for all files in the directory, divided by 2. This number is typically displayed in units of kilobytes (KB). <br>

For example, if the output shows "total 8", it means that the files in the directory occupy a total of 8 blocks on the disk, which could translate to 4 KB of disk space usage. <br>

##### Changing Permissions and Listing Files

```sh
azureuser@titan3:~/linux-commands/Linux-for-Devops$ chmod 777 next
azureuser@titan3:~/linux-commands/Linux-for-Devops$ ls -l
total 8
-rw-rw-r-- 1 azureuser azureuser  183 May 27 09:56 README.md
drwxrwxrwx 2 azureuser azureuser 4096 May 27 12:35 next
```

This is the **Decimal Value Method** for altering the access mode of a file or directory. The value 777 is determined using the table above, granting full access to the directory named 'next'.<br>

##### Changing File Permissions

```sh
azureuser@titan3:~/linux-commands/Linux-for-Devops$ chmod u+rwx README.md
azureuser@titan3:~/linux-commands/Linux-for-Devops$ ls -l
total 8
-rwxrw-r-- 1 azureuser azureuser  183 May 27 09:56 README.md
drwxrwxrwx 2 azureuser azureuser 4096 May 27 12:35 next

azureuser@titan3:~/linux-commands/Linux-for-Devops$ chmod g+rwx README.md
azureuser@titan3:~/linux-commands/Linux-for-Devops$ ls -l
total 8
-rwxrwxr-- 1 azureuser azureuser  183 May 27 09:56 README.md
drwxrwxrwx 2 azureuser azureuser 4096 May 27 12:35 next

azureuser@titan3:~/linux-commands/Linux-for-Devops$ chmod o+rwx README.md
azureuser@titan3:~/linux-commands/Linux-for-Devops$ ls -l
total 8
-rwxrwxrwx 1 azureuser azureuser  183 May 27 09:56 README.md
drwxrwxrwx 2 azureuser azureuser 4096 May 27 12:35 next
```

##### Changing File Permissions

In the scenario above, we grant read, write, and execute access to users, groups, and others accordingly. This method allows us to grant access by name. 

- Use `+` to add access.
- Use `-` to remove access.
- Use `=` to copy access permissions.


# Important Commands

Here is a list of essential command-line utilities for managing and monitoring a Linux system:

## Process Management
- **`ps`**: View information about running processes.

## Disk Usage
- **`df`**: Display disk space usage.
- **`du`**: Show disk usage of files and directories.
  - **`du -sh directory_name`**: Display the total size of the specified directory.

## Process Information
- **`pwdx process_ID`**: Display the working directory of the specified process ID.

## File Transfer and Remote Connection
- **`scp user@192.168.1.100:/path/to/file /local/destination`**: Transfer files between hosts.
- **`ssh [options] [user@]hostname [command]`**: Securely connect to a remote server. Options include `-p` for port specification. You can run a command automatically on the remote server after connecting.

## System Monitoring
- **`htop`**: Monitor running processes in real-time.
- **`iotop`**: Display real-time disk I/O usage by processes.

## Network Utilities
- **`netstat`**: Display network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.
  - **`netstat -a`**: Show both listening and non-listening sockets.
  - **`netstat -at`**: List all TCP ports.
  - **`netstat -au`**: List all UDP ports.
  - **`netstat -l`**: Show only listening ports.
  - **`netstat -lt`**: Show only listening TCP ports.
  - **`netstat -lu`**: Show only listening UDP ports.
  - **`netstat -s`**: Provide statistical information for all ports.
  - **`netstat -pt`**: Display Process ID (PID) and program names associated with network connections.
  - **`netstat -r`**: Retrieve kernel routing information.
  - **`netstat -ap | grep ssh`**: Find the port on which SSH is running.
  - **`netstat -an | grep ':80'`**: Identify the process associated with port 80.
  - **`netstat -i`**: Obtain a list of network interfaces and their activities.

## Disk Partitioning
- **`sudo fdisk -l`**: View all disk partitions.
- **`sudo fdisk -l /dev/sda`**: View partitions on a specific disk (e.g., `/dev/sda`).
- **`sudo fdisk -s /dev/sda`**: View the size of a specific partition (e.g., `/dev/sda`).








