# nexus

### install nexus

{% embed url="https://hub.docker.com/r/sonatype/nexus3/" %}

docker run -d -p 8081:8081 --name nexus sonatype/nexus3

### username password

admin

在container裡面：cat /opt/sonatype/sonatype-work/nexus3/admin.password

改密碼成123456





