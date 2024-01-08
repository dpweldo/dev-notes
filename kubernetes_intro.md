# Kubernetes 
IP & MAC address on Docker are the same. Cannot reachout to eachother. They share the same host IP space, cannot share same port either. Need to recode IP if they die.
### Kubernetes
Master and Worker Nodes

Pods - smallest unit, what holds the IP address, all containers within share. One or many containers. Same IP space as cluster. All nodes can communicate, facilited by network overlay for IP management.

![Title](<Screenshot 2024-01-05 115405.png>)

## Installation 
Complete on all three servers

Setprivlages
~~~ ash
sudo su
~~~
Disable SE Linux
~~~
setenforce 0

sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
~~~
Enable the "br_netfilter" module for cluster communication.
~~~
modprobe br_netfilter

echo '1' > /proc/sys/net/bridge/bridge-nf-call-iptables
~~~
 Disable swap to prevent memory allocation issues.
 ~~~
 swapoff -a

vim /etc/fstab
 ~~~