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

## Monitoring memory usage and availability
The `free` command in Linux is a handy utility used to display information about the system's memory usage and availability. It provides insights into both physical RAM and swap space utilization. Below is a detailed explanation of its usage and output:

The basic syntax of the `free` command is:

```bash
free [options]
```

```bash
$ free -m
             total       used       free     shared    buffers     cached
Mem:          7859       2976       1516       1306        366       2001
-/+ buffers/cache:        607       7252
Swap:         2047          0       2047
```
## Options

- **-b**: Displays memory sizes in bytes.
- **-k**: Displays memory sizes in kilobytes.
- **-m**: Displays memory sizes in megabytes (default option).
- **-g**: Displays memory sizes in gigabytes.
- **-h**: Provides a "human-readable" output with units (e.g., KB, MB, GB).
- **-s [seconds]**: Continuously displays memory usage at specified intervals.
- **-t**: Displays a summary line showing the totals.
- **-l**: Displays low and high memory statistics.
- **-o**: Displays old format (without buffer adjustments).
- **-w**: Wide output, showing more details in the output columns.

## Output Explanation

The `free` command typically outputs the following information:

- **Total**: Total amount of physical RAM in the system.
- **Used**: Amount of RAM currently being used by the system.
- **Free**: Amount of RAM not being used by the system at all.
- **Shared**: Memory used by shared memory objects.
- **Buffer/Cache**: Memory used by the buffer cache and buffers for file I/O.
- **Available**: Estimated amount of memory available for starting new applications, without swapping.
- **Swap**: Information about swap space, including total, used, and free swap space.

In this example:

- The system has a total of 7859 MB of physical RAM.
- 2976 MB is currently in use, leaving 1516 MB free.
- 1306 MB is being shared by shared memory objects.
- Buffers/cache account for 366 MB, with 2001 MB cached.
- The system has 2047 MB of swap space, with none currently in use.


# Text Manipulation

## 1- The sed command
short for "stream editor," is a powerful utility in Linux used for text manipulation. It can perform various operations on text files, such as search and replace, insertion and deletion of lines, and more. Here's a detailed explanation of how to use sed with examples:

The basic syntax of the `sed` command is:

```bash
sed [options] 'command' filename
```
## Options

- [options]: Various options that modify the behavior of sed
- command': The operation to be performed by sed
- filename: The name of the file to be processed


## Common Operations
- **Search and Replace**
To substitute text in a file, use the s command followed by the pattern to search for and the replacement text. The g flag stands for global, replacing all occurrences on each line.
```bash
# Replace "old_text" with "new_text" in example.txt
sed 's/old_text/new_text/g' example.txt
```

- **Insertion and Deletion**
Use the i command to insert text before a specified line number and the d command to delete specific lines.
```bash
# Insert "new_line" before line 5 in example.txt
sed '5i new_line' example.txt

# Delete line 10 from example.txt
sed '10d' example.txt
```

- **Printing**
Print specific lines or ranges of lines from a file using the p command.

```bash
# Print lines 1 to 5 of example.txt
sed -n '1,5p' example.txt
```
- **Pattern Matching**
Perform operations based on pattern matches using regular expressions.

```bash
# Replace "word" with "replaced" only in lines containing "pattern"
sed '/pattern/s/word/replaced/g' example.txt
```
- **Text Transformation**
Transform text in various ways using the y command. For example, convert uppercase to lowercase or vice versa.

```bash
# Convert text to uppercase
sed 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/' example.txt
```

### Example

- Let's consider an example file named "data.txt" containing the following text:


```bash
Hello World
This is a test file
for sed command.
```
- We can perform various operations on this file using sed:
```bash
# Replace "test" with "example"
sed 's/test/example/g' data.txt
```
- sed: Invokes the sed command.
- s: Indicates a substitution operation.
- /test/example/: Specifies the pattern to search for (test) and the replacement text (example).
- g: Stands for global, meaning it replaces all occurrences on each line.
- data.txt: The file on which the operation is performed.

```bash
# Insert "New line" before the second line
sed '2i New line' data.txt
```
- 2i: Specifies line number 2 to insert (i) text before.
- New line: The text to be inserted.
- data.txt: The file on which the operation is performed.

```bash
# Delete the third line
sed '3d' data.txt
```
- 3d: Specifies line number 3 to delete (d).
- data.txt: The file on which the operation is performed.

```bash
# Print lines 1 to 2
sed -n '1,2p' data.txt
```
- -n: Suppresses automatic printing of pattern space.
- 1,2p: Specifies a range of lines (from line 1 to line 2) to print (p).
- data.txt: The file from which lines are printed.

```bash
# Convert text to uppercase
sed 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/' data.txt
```
- y: Indicates a transliteration operation.
- /abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/: Specifies the characters to be replaced with their uppercase equivalents.
- data.txt: The file on which the operation is performed.

## 2- The awk command 
is a versatile text processing tool in Linux that allows you to perform various operations on text files, such as searching, filtering, transforming, and reporting. Here's a detailed explanation of how to use awk with examples:


The basic syntax of the `awk` command is:

```bash
awk 'pattern { action }' filename
```

- pattern: Specifies a condition or pattern to match lines.
- { action }: Defines the action to be performed on lines that match the pattern.
- filename: The input file on which the awk command operates.













