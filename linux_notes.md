# Linux Evolution

## Linux Distributions
Collection of Components that form system
1. Ubuntu
2. Red Hat - commercial market, paid support
3. Debian
4. Fedora
5. CentOS

Tell your linux distribution:
~~~ 
lsb_release -a
~~~
### Elements
1. GUI - desktop environment - kde, unity, xfce
2. X Server - What enables you to use GUI on X server
~~~
X -version
~~~
3. GNU Core Utilities - basic file shell and text manipulation, basic OS commands
~~~
ls --version
~~~
4. Kernal - connects app layer to computer - drivers and system calls, file hierarchy. To get kernel:
~~~
uname -r
~~~

## Linux Embedded Systems
For purpose hardware & software
1. Android
2. Rasberry Pi - Rasbian
3. Consumer Electronics (Modified Open Source Kernel)
4. Networking Equipment - Routers, Switches, WAP, Firewalls

### Components
Hardware - Low Level Interface - Networking & File Systems - High Level Abstraction - Libraries - Application

## Linux Cloud

Cloud 

Region - Location of cloud data centers, independant of other regions

Availability Zones - data centers that comprise a regions, connected to others

Subnet - Local network instance of the compute resource in the cloud

# Major Applications

## Opensource Applications

### Desktop Apps
#### Office Applications
1. OpenOffice - writer, calc, impress, draw
2. LibreOffice - parallel fork of OpenOffice

#### More
1. Firefox
2. Mail Clients - Thunderbirt
3. Gimp - graphic and image application

### Server Applications
#### Web Server
1. Apache HTTP Server - permits conent to be served by host - serves web requests - compiled modules
2. NGINX - reverse proxy, load balancing, mail proxy, and HTTP caching - servers can be between client and backend hosts
#### Database Apps
1. MySQL - LAMP stacks - free easy opensource web stacks - database management system
2. MariaDB - community developed fork of MySQL - claims to be an improvment to MySQL
#### Fileshare Apps
1. Samba - Common Internet File System (CIFS) - commonly used in LAN Samba server - not online - print services or as a client to file server or as server itself
2. NFS - Network File System - a protocol to access files an directories
#### Private Cloud Services
1. ownCloud - application to create your own small coid for file hosting, editing ,and calendar
2. Nextcloud - fork of ownCloud

### Development Languages
1. Shell - run by command line interpriter - BASH is the most common shell in Linux
2. C - Compile for minimum runtime support, imperative - low level, compiled to computer hardware architecture
3. Java - object oriented, compile and run on any machine that has JVM, packaged properly, OpenJDK - free implementation of langauage
4. Javascipt - scripting language that runs on engine - lets you create interactive websites.
5. Perl - general purpose unix language - procedural and object oriented prohgramming - good for patches
6. Python - single method code to complete task, clean syntax, easier to read
7. PHP - web development can be embedded in HTML, and other places

### Package Management tools
Package is collection of files used to install something, finds all your dependecies
#### dpkg: Debian Package
Uses .deb

On debian systems like Ubuntu
~~~
dpkg
~~~
APT - advanced package tool - works with libraries by automating package & dependancies - looks through repositories - usually Ubuntu repo - Ubuntu software center is a GUI of this
~~~
apt-get
~~~
#### rpm: Red Hat Package Manager
Uses .rpm files

Used on Redhat, Fedora, CentOS, SUSE
~~~
rpm
~~~
Has metadata installation path

Yellowdog Updater Modified - yum, utility for rpm based linux systems
A rewrite called DNF has replaced yum on Fedora
~~~
yum
~~~

# Open Source Software and Licensing

## Philosophy
Freedom to use and modify. Source code is available to use and modify to distribute.

Forking is using one project to create a different project.

Permissive Licensing - No restriction on licensing derivative projects

Copyleft - deriviative work must use same license as the original software

## Open Source Licenses

Least to most restrictive

### CCO 1.0 Universal - Public Domain
Anyone can do anything with it, waiving all rights to the work, even for commercial purposes
### MIT
### BSD Licenses
Typically 4 or fewer clauses.
1. Must contain above copyright notice
2. Must retain in binary form
3. Must maintain software attributions
4. Name of original creators cannot be used to endorse or promote derived products
### GPL
Very copy left
Permits commmercial use, modify, and distribute.

Restricts  sublicensing, and must include original work with list of state changes

## Free Software Foundation and Open Source Initiative

### OSI
Should just be available.

### FSF
Only supports pure open source software. Focuses on ethics of rights and restrictions. Freedom to run, to study, redistribute, and distribute modified with no restrictions.

FOSS vs FLOSS - FOSS is free of chareg. FLOSS - is a focus on freedom to use

# Working in Linux
## Desktop Skills
### Versions
LXDE, XFCE, Mate, Cinnamon, Gnome, KDE, Unity

#### User Space and Privacy
Permissions to look, read, modify. Root user has everything on system. Assume with sudo.
#### Features
Can have multiple desktops. Software packages.\

Get hostname
~~~
hostname
~~~

## Industry Uses

Virtualization - all open source and easy

## What distribution is running
~~~
cat /etc/*release*
~~~
~~~
cat /etc/*issue*
~~~
~~~
lsb_release -a
~~~
on system D based distros
~~~
hostnamectl
~~~