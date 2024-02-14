# Kubernetes Quick Start
### Why and Why
Deploys pops that holds the IP address. Pods hold the containers. All containers can communicate, all nodes can communicate as well. 
### Kubernetes Installation
First enter sudo su mode:
~~~shell
sudo su
~~~
Disable SELinux.
~~~shell
setenforce 0

sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
~~~

Enable the "br_netfilter" module for cluster communication.
~~~shell
modprobe br_netfilter
~~~
enable modify iptables
~~~shell
echo '1' > /proc/sys/net/bridge/bridge-nf-call-iptables
~~~
turn off swap
~~~shell 
swapoff -a

vim /etc/fstab
~~~
Comment out the swap line --> 
~~~
# /root/swap swap swap sw 0 0
~~~
Install the Docker prerequisites.
~~~shell   
yum install -y yum-utils device-mapper-persistent-data lvm2
~~~
Add the Docker repo and install Docker.
~~~
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

yum install -y docker-ce
~~~
 Configure the Docker Cgroup Driver to systemd, enable and start Docker
~~~shell    
sed -i '/^ExecStart/ s/$/ --exec-opt native.cgroupdriver=systemd/' /usr/lib/systemd/system/docker.service

systemctl daemon-reload

systemctl enable docker --now 

systemctl status docker

docker info | grep -i cgroup
~~~
 Add the Kubernetes repo.
~~~shell
cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=0
repo_gpgcheck=0
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
      https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
~~~
Install Kubernetes.
~~~shell
yum install -y kubelet-1.14.0 kubeadm-1.14.0 kubectl-1.14.0 kubernetes-cni-0.7.5
~~~
Enable Kubernetes. The kubelet service will not start until you run kubeadm init.
~~~shell
systemctl enable kubelet
~~~

### Master Only Now
Complete the following on the master only:
Initialize the cluster using the IP range for Flannel.

~~~shell
kubeadm init --pod-network-cidr=10.244.0.0/16
~~~
Copy the kubeadm join command. (NOT THIS EXACT ONE)
~~~shell
kubeadm join 172.31.44.27:6443 --token 03z3g0.jezk0s88u2n1efbq     --discovery-token-ca-cert-hash sha256:2c05268c0a3586fb219605cff315a5dbf301a4573678d01c2488d11a47fa0264
~~~
 Exit sudo then run:

~~~shell
exit 

mkdir -p $HOME/.kube

sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

sudo chown $(id -u):$(id -g) $HOME/.kube/config
~~~
Deploy Flannel
~~~shell
kubectl apply -f https://raw.githubusercontent.com/flannel-io/flannel/master/Documentation/kube-flannel-old.yaml
~~~
Check Cluster State
~~~shell 
kubectl get pods --all-namespaces
~~~

### Complete the following on NODES only