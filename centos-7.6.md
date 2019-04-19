# CentOS 7.6

### Host only adapter 

In newer versions of VirtualBox select from **File menu** &gt; **Host network manager**. Add Host only adaptor

### full screen \(x\)

yum install gcc kernel-devel

rpm -qa kernel\* \| sort

yum remove kernel........

sh VBoxLinuxAdditions.sh

reboot 

f1

[https://www.youtube.com/watch?v=YO3Vp8dZIyo](https://www.youtube.com/watch?v=YO3Vp8dZIyo)

e

UTF-8 selinux=0

ctrl + x

vi /etc/selinux/config

SELINUX=disabled



### Copy and Paste\(ok\)

### Network\(ok\)

### SSH

yum install openssh openssh-server

vi /etc/ssh/sshd\_config

AllowUsers 帳號1 帳號2 帳號3

systemctl restart sshd.service

systemctl enable sshd.service

firewall-cmd --permanent --zone=public --add-port=22/tcp

firewall-cmd --reload

virtual box port forward 

### Docker

yum install docker

systemctl start docker

systemctl enable docker

rpm -qa\|grep docker \(查看docker裝了哪些東西\)

### Jenkins

### Gitlab

### Sonarqube













