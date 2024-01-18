# Security
## Basic Security
### Root and Standard Users
Standard Unprivalaged Accounts - provied login shell, home dir, view configs, cannot modify config, granted with `sudo` - super user do

root is often # on line

To become just the root user type `su <username>`
~~~shell
cat /etc/sudoer #shows who has sudo abilities
cat /etc/groups #has sudo group in it, root is always group 0
~~~
~~~shell
/etc/passwd #Username, Password (in shadow), User ID, Group ID, GECOS (long name), Home directory, Login Shell
/etc/shadow #Username, password, lastchanged in days, minimum number of days between changes. maximum number of days between changes, number of days before epire to warn user, number of days since epiiraction (inactive), (expire) absolute expiration date
/etc/groups #username, group name, password (empty), group ID (GID), group list of usernames in the group
groups username #shows you what groups you are in
id username #give UID GID and groups
getent passwd username #gets passwd file line for username
~~~
### System Users
No login shell, separate user from functional privalages and only have services

Service: httpd

user:apache (could be different)

Service: mysqld

user:mysql (could be different)

~~~shell
/user/sbin/nologin #means user cannot login to the shell
~~~
## Creating Users and Groups
### User and Group Commands
Managing users and groups

~~~bash
cat /etc/passwd #see what users are on system, count lines to see counts
sudo useradd username #can add options to speicy UID GID home dir and group membership, you want to create home directory and specify bin bash!
sudo passwd username #sets password for user as password is not set by default
sudo usermod -s /bin/bash #sets shell of user
sudo mkhomedir_helper username #creates home directory for user
sudo useradd -m matt #just creates home directory when creating user
/etc/skel #is the boilerplate file that is created when a new account is made - it populates the home direcotry
~~~
#### Groups
~~~bash
sudo groupadd linuxacademy #creates group
sudo usermod -a -G linuxacadmey username #adds user to group, requires you to reload to show that it was complete
sudo visudo
~~~
### User ID
Local user are given unique ID number. Can have collisions.
~~~bash
UID 0 #UID of root 
UID 1-99 #System users
UID 100+ #standard users
UID 65534 #reserved for user nobody (used to represent user with least permission so you flow from 0 to nobody)
Remote Users #reserved for non local to prevent collisions 
~~~

## File Permissions and Ownership
### File and Directory Permissions

can check out files on `ls -l`

~~~bash
user | group | everyone
7 #Read Write Execute
6 #Read Write
5 #Read Execute
4 #Read
3 #Execute Write
2 #Write
1 #Execute
0 #No Permissions
~~~

~~~bash
chown #lets you change user that owns the file and the group that owns
sudo chown username testfile #changes the user owner
sudo chown :linuxacademy testfile #changes group to linuxacademy
sudo chown username:linuxacademy testfile #changes both
chmod #lets you change the mode of the file read write execute
-R #lets you recursivuly change for both chmod and chown
chmod 644 testfile #changes permissions
chmod g+rw testfile #same changes different permissions
~~~

## Special Directories and Files
### Using Temporary Files and Directories
Used for staging areas that is consistant

~~~bash
/tmp #removed upon system boot, a transient dumping ground for files
/var/tmp  #persists through system boot, up to distro to clear
mktemp #command creats adhoc file or directory with a randomized filename portion these are not automatically removed, usefull to readback into files on shell scripts (can specify options and path and filename template) usually in the /tmp folder
~~~

## Symbolic Links
A link to another file or folder, if original is deleted it does not work anymore
~~~bash
ln -s [target] [linkname] #creates symbolic link on the target file
~~~