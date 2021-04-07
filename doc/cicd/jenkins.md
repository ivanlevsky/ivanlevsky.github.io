### Setup Jenkins
***
Before install jenkins, install [openjdk](../../doc/develop/java.md)  

```shell
#download jenkins from tsinghua mirror site
wget https://mirrors.tuna.tsinghua.edu.cn/jenkins/debian-stable/jenkins_2.277.1_all.deb
#install daemon,net-tools before install jenkins
sudo apt-get install daemon
sudo apt-get install net-tools
#link openjdk to user bin
sudo ln -s /home/zelda/jdk-11/bin/java /usr/bin/java
#install jenkins
sudo dpkg -i /home/zelda/jenkins_2.277.1_all.deb
#check jenkins status
sudo systemctl status jenkins
```
  
  
To unlock jenkins, copy the password in `/var/lib/jenkins/secrets/initialAdminPassword`
```shell
sudo more /var/lib/jenkins/secrets/initialAdminPassword
``` 
```
create jenkins user  
user:jkuser  
pass:jkpass  
```

