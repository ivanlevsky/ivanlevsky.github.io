## Debian Reduce System Size
***
1. Remove non-critical packages  
![remove packages](../../images/system/debian/remove_packages.png "remove packages")  
2. Replace packages with smaller equivalents  
![replace packages](../../images/system/debian/replace_packages.png "replace packages")  
3. Remove other language man files  
![replace language man files](../../images/system/debian/remove_language_man_files.png "remove language man files")  

## Close Gnome Desktop
***  
login into tty3 text terminal mode (press `CTRL+ALT+F3`)  

```shell
# stop gnome graphic login program  
systemctl stop gdm

# check gdm status
systemctl status gdm

# get debian system start mode(gui:graphical.target)
systemctl get-default
```

## Network  
***
reset net ip
```shell
nmcli networking off
nmcli networking on
```
check ip
```shell
ip a
```

ftp server setup
```shell
# install vsftp
sudo apt install vsftpd

# backup vsftp conf file
sudo /etc/vsftpd.conf /etc/vsftpd.conf.bak

# setup vsftp
sudo vi /etc/vsftpd.conf

# set anonymous_enable
anonymous_enable=YES

# uncomment line
write_enable=YES 

# change default port
# uncomment line below
connect_from_port_20=YES
# add line below
listen_port=21

# uncomment three lines below
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list 

# add ftp user, add ftpuser in vsftpd.chroot_list 
sudo vi /etc/vsftpd.chroot_list

# add linux user ftpuser/ftpuserpasswd 
sudo adduser ftpuser 

# check user
more /etc/vsftpd.chroot_list

# check vsftpd conf
sudo cat /etc/vsftpd.conf | grep -v "^#"

# restart VSFTPD service and check the status
sudo systemctl restart vsftpd
sudo systemctl status vsftpd
```

## System
***
restart, stop, start, check status services
```shell
sudo service mysqld restart
sudo service mysqld stop
sudo service mysqld start
sudo service mysqld status

sudo systemctl restart mysqld
sudo systemctl stop mysqld
sudo systemctl start mysqld
sudo systemctl status mysqld
```  
check all exist user
```shell
more /etc/passwd
compgen -u
getent passwd
```
check file size in folder
```shell
du -h 
```
find file in system
```shell
find /folder/abc/...  -name *abc123*
```
check disk space
```shell
df -TH
```
check ram usage and clear cache
```shell
top
echo 3 | sudo tee /proc/sys/vm/drop_caches
```
command like 'll' not working
```shell
#check .bash_profile and add text below
if [ -f ~/.bashrc ];then
     source .bashrc
fi
```
check date time
```shell
current_day=$(date +"%Y%m%d" 2>&1 | cat)
echo $current_day
current_time=$(date +"%H%M%S" 2>&1 | cat)
echo $current_time
```
replace text in file
```shell
sed -i "s/text1/text2/g" filepath
```

### Reference:  
[https://wiki.debian.org/ReduceDebian](https://wiki.debian.org/ReduceDebian)  
[https://wiki.debian.org/FTP ](https://wiki.debian.org/FTP)  
[https://wiki.debian.org/vsftpd](https://wiki.debian.org/vsftpd)  
