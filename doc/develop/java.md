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
export JAVA_HOME=/home/zelda/jdk-11
echo $JAVA_HOME
export PATH=$PATH:$JAVA_HOME/bin
echo $PATH
```

test commands below
```shell
java
javac
java -version
```

