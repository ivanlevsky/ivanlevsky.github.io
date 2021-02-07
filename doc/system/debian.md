## Debian Reduce System Size

1. Remove non-critical packages  
![remove packages](../../images/system/debian/remove_packages.png "remove packages")  
2. Replace packages with smaller equivalents  
![replace packages](../../images/system/debian/replace_packages.png "replace packages") 
3. Remove other language man files  
![replace language man files](../../images/system/debian/remove_language_man_files.png "remove language man files")

## Close Gnome Desktop:
login into tty3 text terminal mode(`CTRL+ALT+F3`)
```shell script
#stop gnome graphic login program  
systemctl stop gdm  
#check gdm status
systemctl status gdm  
#get debian system start mode(gui:graphical.target)
systemctl get-default  
```

## Reset Net Ip:
```shell script
   nmcli networking off
   nmcli networking on
```
ip a
Reference:  
https://wiki.debian.org/ReduceDebian
