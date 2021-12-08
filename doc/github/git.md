### Setup Git
***
```shell
# install git
sudo apt-get install git

# set user, name, email
git config --global user "ivanlevsky"
git config --global user.name "ivanlevsky"
git config --global user.email "ivanlevsky@gmail.com"

# use this to fix git push ssl error 10054
git config --global http.sslVerify "false"
```

### Use Git
***
clone repo
```shell
git clone https://github.com/ivanlevsky/ivanlevsky.github.io.git
```
  
set ssh key in new computer
```shell
# generate ssh key
ssh-keygen -t rsa -b 4096 -C "ivanlevsky@gmail.com"

# copy public key in id_rsa.pub to github, add SSH keys in github setting page
cat ~/.ssh/id_rsa.pub

# test ssh key
ssh -T git@github.com
```
  
check git commit history
```shell
cd ../git project dir/
git log
```

delete commit log
```shell
cd ../git project dir/
git reset --hard commit id
```