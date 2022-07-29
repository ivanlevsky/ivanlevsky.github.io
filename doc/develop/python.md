### Setup Python
***
install required packages
```shell
sudo apt update
sudo apt install build-essential zlib1g-dev \
libncurses5-dev libgdbm-dev libnss3-dev \
libssl-dev libreadline-dev libffi-dev curl
```
download python install package
```shell
wget https://www.python.org/ftp/python/3.10.5/Python-3.10.5.tgz
```
unzip python install package
```shell
tar -xf Python-3.10.5.tgz
```
configure the script
```shell
cd Python-3.*
./configure --enable-optimizations 
```
start install process keep old python version
```shell
sudo make altinstall
```
start install process replace old python3 version, remove old version first
```shell
sudo apt remove python3.**
sudo make install
```
install python module
```shell
pip3 instal xxxx --no-cache-dir
```
