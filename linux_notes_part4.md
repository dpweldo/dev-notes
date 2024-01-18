# Operating System
## Chosing an Operating System
### OS Differences
1. Linux - Open Source, Free, Supports all Hardware, Bash, Muiltiple GUI
2. MacOS - Proprietary, Free, Hardware Lock, Bash, macOS GUI
3. Windows - Proprietary, Costs, Okay Hardware Support, Powershell, WindowsOS

### Distribution Lifecycle Management
Release Models:
#### Standard Distribution Release (More Stable)
Made availaible and then frozen to make sure all bugs and such are taken care of. Usually point release model.
 

~~~shell
uname -r #shows the kernel version
4.15.0-50-generic
cat /etc/issue #shows the issue of the distribution that you have
Ubuntu 18.04.2 LTS #Shows valid version that has consistent update and supports 18 is day 4 is month LTS means long term support
~~~
#### Rolling Release (More Cutting Edge)
Small releases that have frequent updates to the core and added as they arrive. 

Archlinux - does not have versions - just is the latest version
Gen2 same.

## Hardware
~~~bash
cat /proc/cpuinfo #gives info on CPU
~~~

~~~bash 
cat /proc/cpuinfo #CPU
cat /proc/loadavg #gives system load
free -m #RAM info and info on swap (HDD RAM)
df -h #HDD/SSD/DVD storage info
ifconfig #NIC to show interfaces of NIC lo is a loopback address
sudo dmidecode #dumps information from motherboard
sudo lshw #information on hardware and firmware BIOS
#Mouse/Keyboard
#Monitor
~~~
Drivers- reside in the running kernel and enable OS to use hardware

## Where Data Is Stored
### Programs and Configuration (common locations for sys and config data)
Usually in `/etc`, `boot` is another place
~~~shell
/boot
grub #ubuntu boot loader
vmlinzu #kernel files
memtest #utility for testing ram
config #is the config for the kernel
~~~
~~~shell
/etc
/fstab #what disk partitions to mount at the root level and where in the file system
    blkid #shows UUID to check on file
/passwd #username, password (hash moved to /etc/shadow), userID, groupID, home directory, and loginshell
/group #group name, password, groupID, member of groups
/hosts #mapping of ip addresses to host names so on command line if you want your own DNS
/resolve.conf #where you specify name server
/vimrc #vim config
/<APPLICAION> #where you find application configs
~~~
Another place is in /sys
~~~shell
sysfs #ram file system completly on ram used to export info of subsystems (kernel)
~~~

### Processes
Data used by running proccess.

Process ID: `PID`

You can get a snapshot with the `ps` command.
~~~bash
/proc/<PID>/ #shows process data with folders that show information and status
ps aux #shows you all infor on the system using BSD syntax
ps -eF #List all processes Linux format
ps -U <username> #gives processes being run by effective user
ps -u <username> #gives processes being run by actual user

~~~

~~~shell
top #allows you to sort and look at running processes and resource ussage & priority
~~~

~~~shell
/sys #Device data with system information and attached hardware
/dev #contains files with character or block devices - so Linux can treat device as a file
~~~

### System Messaging - Viewing and accessing system messages
Kernel Ring Buffer - where messages come from - new messages come in and push out old (buffer)

~~~bash
dmesg #used for looking at kernel specific information
~~~

### Logging
Common locations for sys and app log data

Log Daemon - system logging protocol `syslog` `rsyslogd` -service that performt the message collection


~~~bash
/var/log/syslog  # date and timestamp of general logs
/var/log/messages #Same but for Debian

/var/log/auth.log #authentication log, timestamp, user, auth module, session info, CRON (daemon that execute things on an interval can set commands to run on intervals too - pretty cool)
/var/log/secure #same but for Red Hat

/var/log/boot.log #system boot logs
/var/log/cron.log #cron job logs
/var/log/kern.log #Kernel Logs
/var/log/faillog #Authentication Fail Logs - very imporatnt for security
~~~

## Networks
### Your Computer on the Network
Device - Switch - Router (Gateway)

~~~shell
ip addr show #gives list of IP addresses of NIC and local
~~~
~~~shell
ping #sends ICMP request to host
~~~
~~~shell
curl #like ping but not blocked as often
~~~

### DNS Client Configuration
Maps domain names to IP addresses.

~~~shell
dig www.linuxacademy.com # gives you IP address of internet A record Gives alot of info like what server was used
dig @1.1.1.1 www.linuxacademy.com #asks the DNS server of 1.1.1.1
/etc/resolve.conf # config file that determines which host to use for DNS queries. 
/etc/hosts #used for statically mapping ap addresses to hostnames such as localhost
~~~
~~~shell
host www.example.com #another command to show ip address of domain name, more simple result
host www.example.com 1.1.1.1
~~~

### Network Configuration
Address Configuration
~~~shell
ip route show #shows the default routing table (send default to router ecept on local to ens33 (local) NICs and such)
~~~~
~~~shell
ip addr show #shows the current addresses
~~~
~~~shell
ifconfig # old school way to change the interface confiuration and devices
nmcli #also shows your devices
~~~
~~~shell
netstat #view active conncetions to see connections
netstat -tlnp #- TCP Listening Numeric (IP) and port
cat /etc/services | grep 22 #investigate what port 22 is
ss #very similar to netstat
~~~
