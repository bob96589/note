# Centos Env

After struggling for almost a day, I found out that maven is not reading the `$JAVA_HOME` from

```text
 ~/.bashrc
 ~/.bash_profile
 ~/.profile
```

but it reads `$JAVA_HOME` from `~.mavenrc`

so finally, when I added

```text
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_141.jdk/Contents/Home
```

in `~.mavenrc` then got output

```text
mvn -v
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=1024m; support was removed in 8.0
Apache Maven 3.5.0 (ff8f5e7444045639af65f6095c62210b5713f426; 2017-04-03T15:39:06-04:00)
Maven home: /usr/local/Cellar/maven/3.5.0/libexec
Java version: 1.8.0_141, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk1.8.0_141.jdk/Contents/Home/jre
Default locale: en_CA, platform encoding: UTF-8
OS name: "mac os x", version: "10.12.6", arch: "x86_64", family: "mac"
```

