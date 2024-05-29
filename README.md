# Linux-for-Devops
This repository is created to provide a basic understanding of Linux commands and related notes required for the field of DevOps and Cloud Infrastructure services.


# File and Directory Operations Commands

**ls**  :  list files and directories<br>
**ls -l**  :  displays files and directories with detailed information<br>
**ls -a**  :  shows all files and directories, including hidden files<br>
**ls -h**  :  displays file sizes in a human-readable format<br>
**cd**  :  change directory cd /path/to/directory<br>
**pwd**  :  displays current working directory<br>
**mkdir**  :  creates a new directory. mkdir new_directory_name<br>
**rmdir**  :  remove directory<br>
**rm**  :  remove files <br>
**cp**  :  copy files and directories<br>
**mv**  :  Move/rename files and directories<br>
**touch**  :  create an empty file or update file timestamps<br>
**cat**  :  view the content of a file<br>
**cat > file_name**  :  Append and overwrite text in to a file (use CNTRL+D) to exit<br>
**cat >> file_name**  :  Append without overwriting text in to a file (use CNTRL+D) to exit<br>
**cat f1 f2 > f3**  :  concatenate texts of files f1 and f2 and creating new file f3 with all text<br>
**head**  :   Display the first few lines of a file.<br>
**head -n 5 file_name**  :  Displays the first five lines of the file<br>
**tail**  :   Display the last few lines of a file.<br>
**tail -n 5 file_name**  :  Displays the last five lines of the file<br>
**find**  :  search file by name (-name) / by type (-type)<br>
**hostname**  :  Displays Machine name<br>
**hostname -i**  :  Displays the private IP address<br>
**cat /etc/os-release**  :  Displays OS version and details<br>
**whoami**  :  Displays current user<br>

# File Permission Commands

**chmod**  :  to change the access modes of a file<br>
**chown**  :  change the owner of the file or directory<br>
**chgrp**  :  change group of a file or directory<br>


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

**ps**  :  command-line utility for viewing information about processes running on a systemr<br>
**df**  :  command-line utility for displaying disk space usage on Linux systems<br>
**du**  :  command-line utility for displaying disk usage of files and directories<br>
**du -sh directory_name**  :  Displays the total size of the specified directory<br>
**pwdx process_ID**  :  Dispalys working directory of given process ID<br>
**scp user@192.168.1.100:/path/to/file /local/destination**  :  Transfer files between hosts<br>
**ssh [options] [user@]hostname [command]**  :  to connect securely with remote server. Options: are (-p: port), command: after connecting this command will be run automatically on remote server<br>
**htop**  :  to monitor running processes on realtime<br>
**iotop**  :  displays real-time disk I/O usage by processes<br>
**netstat**  :  command-line network utility that displays network connections, routing tables, interface statistics, masquerade connections, and multicast memberships<br>
**netstat -a**  :  Show both listening and non-listening sockets<br>
**netstat -at**  :  specifically lists all TCP ports, giving you information about the TCP connections your system is engaged in<br>
**netstat -au**  :  focuses on UDP ports, revealing details about UDP connections<br>
**netstat -l**  :  shows only the ports that are actively listening for incoming connections<br>
**netstat -lt**  :  Narrowing it down further, this command specifically lists the TCP ports that are in a listening state<br>
**netstat -lu**  :  this command focuses on displaying only the UDP ports that are actively listening<br>
**netstat -s**  :  provides statistical information for all ports, offering insights into network activity<br>
**netstat -pt**  :  This option enriches the output by displaying Process ID (PID) and program names associated with network connections<br>
**netstat -r**  :  This command retrieves kernel routing information, displaying destination addresses, gateways, and interface details<br>
**netstat -ap | grep ssh**  :  To find the port on which a specific program, in this case, SSH, is running, use this command<br>
**netstat -an | grep ':80'**  :  This command helps identify the process associated with a given port, such as port 80 in this example<br>
**netstat -i**  :  Use this command to obtain a list of network interfaces, providing details about each interface’s activities<br>







