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

### sudo

is not in the sudoers file. This incident will be reported

su

chmod u+w /etc/sudoers

vi /etc/sudoers

xxx ALL=\(ALL\) ALL

chmod u-w /etc/sudoers

### Docker

yum install docker

systemctl start docker

systemctl enable docker

rpm -qa\|grep docker \(查看docker裝了哪些東西\)



### dial unix /var/run/docker.sock: connect: permission denied

groupadd docker

ls -la /var/run/docker.sock

chown :docker /var/run/docker.sock

usermod -g docker user



Change the owner of a file: chown root file

Change the group of a file: chown :friends file

### Firewall

su

firewall-cmd --zone=public --add-port=6379/tcp --permanent 

firewall-cmd --zone=public --add-port=8000-9999/tcp --permanent 

firewall-cmd --reload 

firewall-cmd --zone=public --list-all

### Jenkins

jenkins on centos: [https://oranwind.org/-devops-jenkins-an-zhuang-jiao-xue/](https://oranwind.org/-devops-jenkins-an-zhuang-jiao-xue/)

jenkins on docker: [https://ithelp.ithome.com.tw/articles/10200621?sc=iThelpR](https://ithelp.ithome.com.tw/articles/10200621?sc=iThelpR)

sudo mkdir -p /data/jenkins

sudo chown -R $USER:$GROUP /data

docker run  --name jenkins  -d --restart always  -p 9003:8080 -p 50000:50000  -v /data/jenkins:/var/jenkins\_home  jenkins/jenkins:lts

localhost:9003

cat /data/jenkins/secrets/initialAdminPassword

admin/admin

### Gitlab

gitlab on docker: [https://blog.toright.com/posts/5831/%E4%B8%89%E7%A7%92%E6%95%99%E4%BD%A0%E7%94%A8-docker-%E5%AE%89%E8%A3%9D-gitlab.html](https://blog.toright.com/posts/5831/%E4%B8%89%E7%A7%92%E6%95%99%E4%BD%A0%E7%94%A8-docker-%E5%AE%89%E8%A3%9D-gitlab.html)

sudo docker run --detach --hostname gitlab.example.com --publish 443:443 --publish 9004:80 --name gitlab --restart always --volume /gitlab/config:/etc/gitlab --volume /gitlab/logs:/var/log/gitlab --volume /gitlab/data:/var/opt/gitlab  gitlab/gitlab-ce:latest

root/P@ssw0rd

### PostgreSQL



### Sonarqube













