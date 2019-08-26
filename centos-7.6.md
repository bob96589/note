# CentOS 7.6

### Host only adapter 

In newer versions of VirtualBox select from **File menu** &gt; **Host network manager**. Add Host only adaptor

### VMSVGA

VirtualBox預設顯示模式為VMSVGA



### full screen \(o\)

{% embed url="https://wiki.centos.org/HowTos/Virtualization/VirtualBox/CentOSguest" %}

yum install dkms

yum groupinstall "Development Tools" 

yum install kernel-devel

安裝的版本要相同

### full screen \(x\)

yum install gcc kernel-devel

rpm -qa kernel\* \| sort

yum remove kernel........

sh VBoxLinuxAdditions.sh

VirtualBox預設顯示模式為VMVGA

reboot 

f1

[https://www.youtube.com/watch?v=YO3Vp8dZIyo](https://www.youtube.com/watch?v=YO3Vp8dZIyo)

boot server, press "e"

at the end ot the "linux16" line : added selinux=0 \(to disable SELinux and allow boot to succeed as described by Terrence\)

ctrl+x

login to server and reinstall selinux-policy-targeted

yum reinstall selinux-policy-targeted

touch /.autorelabel

systemctl reboot

after reboot check SELinux status

sestatus

  
**★★ 暫時性的關掉或開啟 selinux ★★** 

$ getenforce  
Enforcing  
$ sudo setenforce 0  
$ getenforce  
Permissive  
$ sudo setenforce 1  
$ getenforce  
Enforcing  


**★★ 永久性的關掉 selinux ★★** 

$ sudo vi /etc/sysconfig/selinux     

找到  
SELINUX=enforcing  
然後修改為  
SELINUX=disabled  
要重新開機 reboot / restart 後才會套用



### Copy and Paste\(ok\)

### Network\(ok\)

### SSH

yum install openssh openssh-server

vi /etc/ssh/sshd\_config

AllowUsers 帳號1 帳號2 帳號3

systemctl restart sshd.service

systemctl enable sshd.service \(設定下次開機時，後面接的 unit 會被啟動\)

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



sudo vi /etc/sudoers 

或 

sudo visudo 就是去編輯設定檔。

將這行 %sudo ALL=\(ALL:ALL\) ALL 改成 %sudo ALL=\(ALL:ALL\) NOPASSWD:ALL

### sharedFolder

```text
sudo yum install git
```

![](.gitbook/assets/tu-pian-152.png)

don't need to shutdown   
mkdir /mnt/shareFolder   
mount -t vboxsf shareFolder /mnt/shareFolder   
mount.vboxsf shareFolder /mnt/shareFolder   
mounting failed with the error: Protocol error   
不要選自動掛載   
modprobe vboxvfs

### View hidden file

ctrl + h



### Git

sudo yum install git

git --version



### Docker

yum install docker

systemctl start docker

systemctl enable docker

rpm -qa\|grep docker \(查看docker裝了哪些東西\)

is-active ：目前有沒有正在運作中 

systemctl is-active docker

is-enabled：開機時有沒有預設要啟用這個 unit

systemctl is-enabled docker



sudo groupadd docker

sudo usermod -G docker -a user

sudo systemctl restart docker

### remove docker

sudo yum remove docker docker-common docker-selinux docker-engine

### upgrade docker

$ sudo yum -y update

$ sudo curl -sSL [https://get.docker.com](https://get.docker.com) \| sh

$ sudo systemctl enable docker

$ sudo systemctl start docker

$ sudo ps aux \|grep docker

$ sudo systemctl status docker

### install docker compose

[https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

sudo curl -L "[https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$\(uname](https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$%28uname) -s\)-$\(uname -m\)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

docker-compose --version



### dial unix /var/run/docker.sock: connect: permission denied

groupadd docker

ls -la /var/run/docker.sock

chown :docker /var/run/docker.sock

usermod -g docker user



Change the owner of a file: chown root file

Change the group of a file: chown :friends file

chown -R user:user file

recursive change??????????????

### Firewall

su

firewall-cmd --zone=public --add-port=6379/tcp --permanent  
firewall-cmd --zone=public --add-port=8000-9999/tcp --permanent  
firewall-cmd --reload  
firewall-cmd --zone=public --list-all

### Docker run command parameter

--restart always  

docker pull jenkins/jenkins:lts gitlab/gitlab-ce:latest postgres:latest sonarqube

### Jenkins

jenkins on centos: [https://oranwind.org/-devops-jenkins-an-zhuang-jiao-xue/](https://oranwind.org/-devops-jenkins-an-zhuang-jiao-xue/)  
jenkins on docker: [https://ithelp.ithome.com.tw/articles/10200621?sc=iThelpR](https://ithelp.ithome.com.tw/articles/10200621?sc=iThelpR)

sudo mkdir -p /app/jenkins  
sudo chown -R $USER:$GROUP /app/jenkins

windows /app -&gt; /c/Users/app

docker run -d \  
--name jenkins \  
--network myNetwork \  
-p 9003:8080 \  
-p 50000:50000 \  
-v /app/jenkins:/var/jenkins\_home \  
jenkins/jenkins:lts

localhost:9003  
cat /app/jenkins/secrets/initialAdminPassword  
admin/admin

Global Tool Configuration/Maven installations/Install automatically  
-f ./source/ckms clean package -U sonar:sonar -Dsonar.host.url=[http://sonarqube:9000](http://sonarqube:9000) -Dsonar.sourceEncoding=UTF-8

![](.gitbook/assets/tu-pian-153%20%281%29.png)

sonar:sonar -Dmaven.test.skip=ture -Dsonar.host.url=[http://sonarqube:9000](http://sonarqube:9000) -Dsonar.sourceEncoding=UTF-8 -Dsonar.login=3596ad9b3c7fb2e855d739389ffa4234d2be29a0

### Gitlab

gitlab on docker: [https://blog.toright.com/posts/5831/%E4%B8%89%E7%A7%92%E6%95%99%E4%BD%A0%E7%94%A8-docker-%E5%AE%89%E8%A3%9D-gitlab.html](https://blog.toright.com/posts/5831/%E4%B8%89%E7%A7%92%E6%95%99%E4%BD%A0%E7%94%A8-docker-%E5%AE%89%E8%A3%9D-gitlab.html)

sudo mkdir -p /app/gitlab/config /app/gitlab/logs /app/gitlab/data  
sudo chown -R $USER:$GROUP /app/gitlab

sudo docker run --detach \  
--hostname gitlab.example.com \  
--publish 443:443 \  
--publish 9004:80 \  
--name gitlab \  
--network myNetwork \  
--volume /app/gitlab/config:/etc/gitlab \  
--volume /app/gitlab/logs:/var/log/gitlab \  
--volume /app/gitlab/data:/var/opt/gitlab \  
gitlab/gitlab-ce:latest

localhost:9004  
root/P@ssw0rd

### PostgreSQL

docker network create myNetwork  
docker network list

sudo mkdir -p /app/postgres  
sudo chown -R $USER:$GROUP /app/postgres

docker run -d \  
--name postgres \  
--network myNetwork \  
-p 9006:5432 \  
-v /app/postgres:/var/lib/postgresql/data \  
-e POSTGRES\_DB=sonar \  
-e POSTGRES\_USER=admin \  
-e POSTGRES\_PASSWORD='admin' \  
postgres:latest

### Sonarqube

docker run -d \  
--name sonarqube \  
--network myNetwork \  
-p 9005:9000 \  
-e sonar.jdbc.username=admin \  
-e sonar.jdbc.password=admin \  
-e sonar.jdbc.url="jdbc:postgresql://postgres:5432/sonar" \  
sonarqube

localhost:9005

admin/admin





### Host

cat /etc/hosts





