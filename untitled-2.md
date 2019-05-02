# docker toolbox

docker pull jenkins/jenkins:lts gitlab/gitlab-ce:latest postgres:latest sonarqube

### docker network

docker network create myNetwork  
docker network list

### Jenkins

jenkins on centos: [https://oranwind.org/-devops-jenkins-an-zhuang-jiao-xue/](https://oranwind.org/-devops-jenkins-an-zhuang-jiao-xue/)  
jenkins on docker: [https://ithelp.ithome.com.tw/articles/10200621?sc=iThelpR](https://ithelp.ithome.com.tw/articles/10200621?sc=iThelpR)

sudo mkdir -p /c/Users/bob/app/jenkins  
sudo chown -R $USER:$GROUP /c/Users/bob/app/jenkins

windows /app -&gt; /c/Users/bob/app

docker run -d \  
--name jenkins \  
--network myNetwork \  
-p 9003:8080 \  
-p 50000:50000 \  
-v /c/Users/bob/app/jenkins:/var/jenkins\_home \  
jenkins/jenkins:lts

localhost:9003  
cat /c/Users/bob/app/jenkins/secrets/initialAdminPassword  
admin/admin

Global Tool Configuration/Maven installations/Install automatically  
-f ./source/ckms clean package -U sonar:sonar -Dsonar.host.url=[http://sonarqube:9000](http://sonarqube:9000) -Dsonar.sourceEncoding=UTF-8

![](.gitbook/assets/tu-pian-153%20%281%29.png)

sonar:sonar -Dmaven.test.skip=ture -Dsonar.host.url=[http://sonarqube:9000](http://sonarqube:9000) -Dsonar.sourceEncoding=UTF-8 -Dsonar.login=3596ad9b3c7fb2e855d739389ffa4234d2be29a0

### Gitlab

gitlab on docker: [https://blog.toright.com/posts/5831/%E4%B8%89%E7%A7%92%E6%95%99%E4%BD%A0%E7%94%A8-docker-%E5%AE%89%E8%A3%9D-gitlab.html](https://blog.toright.com/posts/5831/%E4%B8%89%E7%A7%92%E6%95%99%E4%BD%A0%E7%94%A8-docker-%E5%AE%89%E8%A3%9D-gitlab.html)

sudo mkdir -p /c/Users/bob/app/gitlab/config /c/Users/bob/app/gitlab/logs /c/Users/bob/app/gitlab/data  
sudo chown -R $USER:$GROUP /c/Users/bob/app/gitlab

? volume 用不上去，只好用這個寫法，不是很好  
docker volume create gitlab\_config  
docker volume create gitlab\_logs  
docker volume create gitlab\_data

docker run --detach \  
--hostname gitlab.example.com \  
--publish 443:443 \  
--publish 9004:80 \  
--name gitlab \  
--network myNetwork \  
--volume gitlab\_config:/etc/gitlab \  
--volume gitlab\_logs:/var/log/gitlab \  
--volume gitlab\_data:/var/opt/gitlab \  
gitlab/gitlab-ce:latest

localhost:9004  
root/P@ssw0rd

### PostgreSQL

sudo mkdir -p /c/Users/bob/app/postgres  
sudo chown -R $USER:$GROUP /c/Users/bob/app/postgres

docker volume create postgres\_data

docker run -d \  
--name postgres \  
--network myNetwork \  
-p 9006:5432 \  
-v postgres\_data:/var/lib/postgresql/data \  
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





