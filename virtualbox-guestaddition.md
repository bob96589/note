# VirtualBox GuestAddition

unknown filesystem type 'iso9660'

```text
yum update
yum upgrade
可以用命令cat /proc/filesystems查看是否有iso9660，有的話就可以了
```

remove old unused kernels on CentOS

```text
# rpm -q kernel
kernel-3.10.0-327.36.3.el7.x86_64
kernel-3.10.0-514.2.2.el7.x86_64
kernel-3.10.0-693.5.2.el7.x86_64

# yum remove kernel-3.10.0-327.36.3.el7.x86_64

# rpm -qa kernel\* | sort
```



