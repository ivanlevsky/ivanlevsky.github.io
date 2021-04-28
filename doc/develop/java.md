### Setup OpenJDK  
***
download openjdk and extract it, move jdk folder to `/home/user` directory   
```shell
cd /home/zelda/
wget https://download.java.net/openjdk/jdk11/ri/openjdk-11+28_linux-x64_bin.tar.gz
tar xvf openjdk-11+28_linux-x64_bin.tar.gz
```
  
set java home environment
```shell
sudo vi /etc/profile
# add line 'export JAVA_HOME=/home/zelda/jdk-11'
# add '$JAVA_HOME/bin' in PATH
source /etc/profile
# test JAVA_HOME and PATH
echo $JAVA_HOME
echo $PATH
```

test commands below
```shell
java
javac
java -version
```

