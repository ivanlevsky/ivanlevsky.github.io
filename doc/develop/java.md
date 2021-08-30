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

run java package source, create classes folder in package
```shell
cd project folder
mkdir classes
javac -d classes src\com\java\common\DateUtils.java
java -classpath ./classes com/java/common/DateUtils

# use third party libs
javac -cp lib\mysql-connector-java-5.1.21-bin.jar;lib\log4j-1.2.17.jar -d classes src\com\java\common\DatabaseUtils.java
# compile jar file, create manifest.txt in project path:
# Main-Class: com.java.common
# Class-Path: lib\mysql-connector-java-5.1.21-bin.jar
# <blank line>
jar cfm DateUtils.jar manifest.txt -C classes com
java -jar DateUtils.jar
```
