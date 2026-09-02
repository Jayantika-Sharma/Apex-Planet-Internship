# Linux Fundamentals
Users:
1. Regular User
2. Root User(ADMIN)
3. Service User

## Other: 
- `Ctrl + Alt + T` -> Open Terminal
- `man <command>` -> Displays the manual of a command.
- `mkdir <name>` ->To create a new directory\
- `touch <file_name with extenstion>` -> To create file
- `cp [-r] <orginal> <copied>` -> To copy file and folder(-r)
- `mv <file> <new_path>` -> To move one file to another directory.
- `rm [-r] <file>` -> To remove file or non empty directory.
- `rmdir <folder>` -> To remove directory
- `history` -> Displays previously executed commands.
- `/` -> Represents the root directory.
- `.` -> Represents the current directory.
- `..` -> Represents the parent directory.
- `sudo` -> Executes a command with administrative privileges.
- `sudo su -` -> Switches to the root user with a root login environment.
- `printf` -> Displays formatted text.
- `top` -> Displays real-time system resource and process information.
- `ps` -> Displays information about running processes.
- `kill` -> Sends a signal to a process using its PID.
<hr>

## 1. File System Navigation
- `cd <name>`-> To change Directory
/:ROOT
~:Home directory
-:Change tp previous directory
- `pwd` -> Print working directory/Display the current working directory
- `ls [-<a/l/h/t/r>]` -> Lists files and directories.<br>
a:Show Hidden file<br>
l:Show in Long Format<br>
h:Display size in readable format<br>
t:Sort by time(newest first)<br>
r:Reverse order of t<br>
- `ls --sort=<text>` -> Sorts files according to the specified field.
<hr>

## 2. File & Directory Permissions (chmod, chown)
**Permission**
- *Group*:
1. Owners
2. Group 
3. Others
4. All

- *Permission*
1. read (r)
2. write (w)
3. execute (x)

- *Permission Value*<br>
rwx = bin(111)= 7<br>
rw- = bin(110)= 6<br>
r-x = bin(101)= 5<br>
r-- = bin(100)= 4<br>
-w- = bin(010)= 2<br>
--x = bin(001)= 1<br>
--- = bin(000)= 0<br>

- `chmod` -> To change permission
chmod <value_owner><value_group><value_others>  <file/folder>
To *add* Permission
chmod <Group>+<permission_add> <file>
To *remove* Permission
chmod <Group>-<permission_remove> <file>

- `chown` -> To change ownership
*sudo chown [-r] <owner>[<:group>] <folder>/*
<hr>

## 3. Package Management (apt, dpkg)
**apt**
- `sudo apt update` -> Updates the package information from repositories.
- `sudo apt-get update` -> Updates the package information from repositories.
- `sudo apt upgrade` -> Upgrade installed packages
- `sudo apt install <package-name>` -> To install package
- `apt search <package>` -> To search a package
- `apt show <package>` -> To show a package
- `sudo apt purge <package>` -> To remove a package and configuration files.
- `sudo apt autoremove` -> To clean unused package
**dpkg**
- `sudo dpkg -i <package.deb>` -> To install package
- `dpkg -l` -> To list installed packages
- `dpkg -l | grep <package>` -> To find specific package
- `dpkg -s <package>` -> To show package information
- `sudo dpkg -r <package>` -> To remove a package
<hr>

## 4. Networking Commands (ifconfig, ping, netstat, traceroute)
- `ifconfig` ->
It can show:
1. Network interface
2. IP address
3. MAC address
4. Network status

- `ping <ip address/dns>`-> Tests connectivity between your system and another host.
ctrl+c - To quit

- `netstat <-a/t/u/l/n> or <tuln>`<br>
a:All connections<br>
t:TCP connections<br>
u:UDP connections<br>
l:Listening sockets<br>

- `traceroute <destination>` -> It shows the path packetes took towards destinations.

