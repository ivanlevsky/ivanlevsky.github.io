### Setup Docker
***

![install_docker](../../images/cicd/docker/install_docker.png)  

***    
```shell 
# download docker deb file
wget https://download.docker.com/linux/debian/dists/buster/pool/stable/amd64/docker-ce_20.10.5~3-0~debian-buster_amd64.deb
```
![download_docker_deb](../../images/cicd/docker/download_docker_deb.png)

```shell
# download contained.io deb  
wget https://download.docker.com/linux/debian/dists/buster/pool/stable/amd64/containerd.io_1.4.3-1_amd64.deb
```
![download_contained_io](../../images/cicd/docker/download_contained_io.png)

```shell
# download docker-ce-cli deb
wget https://download.docker.com/linux/debian/dists/buster/pool/stable/amd64/docker-ce-cli_20.10.5~3-0~debian-buster_amd64.deb
```

install `containerd.io` , `docker-ce-cli` before install docker deb file, 
```shell
# install containerd, docker-ce-cli, docker-ce debs
sudo dpkg -i /home/zelda/Downloads/containerd.io_1.4.4-1_amd64.deb
sudo dpkg -i /home/zelda/Downloads/docker-ce-cli_20.10.5_3-0_debian-buster_amd64.deb
sudo dpkg -i /home/zelda/Downloads/docker-ce_20.10.5~3-0~debian-buster_amd64.deb
```

![install_docker_ce_cli](../../images/cicd/docker/install_docker_ce_cli.png)
![install_contained_io](../../images/cicd/docker/install_contained_io.png)
![install_docker_ce](../../images/cicd/docker/install_docker_ce.png)
other install method check:  
[https://docs.docker.com/engine/install/debian/](https://docs.docker.com/engine/install/debian/)  

Verify that Docker Engine is installed correctly by running the hello-world image  
![check_docker_cmd](../../images/cicd/docker/check_docker_cmd.png)
![run_docker_hello_world](../../images/cicd/docker/run_docker_hello_world.png)  

### Use Docker Command
***
```shell
# list all images
sudo docker images -a

# list all containers
sudo docker ps -a
sudo docker container ls -a

# delete a container
sudo docker rm -f 

# clear docker cache use in linux memory
echo 3 | sudo tee /proc/sys/vm/drop_caches
```

### Reference:    
[docker commands](https://docs.docker.com/engine/reference/run/)  
[docker_lauguage_set](https://docs.docker.com/language/)  
[docker_cicd](https://docs.docker.com/ci-cd/best-practices/)  