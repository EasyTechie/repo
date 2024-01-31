# Docker
Install Docker on Ubuntu (AWS) and Verify Hello-World

## Focus
1. Update Ubuntu System
2. Uninstall any docker footage
3. Install docker
4. Verify with Hello-World

## Assumptions:
- setup is based on `root` user access.
- OS is Ubuntu 20.04 version - confirm by running the command: **_lsb_release -a_**
```
whoami
lsb_release -a
```
      No LSB modules are available.
      Distributor ID: Ubuntu
      Description:    Ubuntu 20.04.6 LTS
      Release:        20.04
      Codename:       focal
  
---

## 1. Update Ubuntu system to latest
```
sudo su -
apt update -y
apt upgrade -y
```

## 2. Commands for Uninstalling any docker footage 

1. Remove existing docker related packages if exists any.
```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do apt-get remove $pkg; done
apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
```

2. Clean up any existing storage files if exists any.
```
rm -rf /var/lib/docker
rm -rf /var/lib/containerd
```

## 3. Commands for Installing using the _apt_ repository

### Add Docker's official GPG key:
```
apt-get update
apt-get install ca-certificates curl gnupg
install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
chmod a+r /etc/apt/keyrings/docker.gpg
```

### Add the repository to Apt sources:
```
echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    tee /etc/apt/sources.list.d/docker.list > /dev/null
apt-get update
```

### Install the Docker packages
```
apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

## 4. To check the status of Docker running or not
On Debian and Ubuntu, the Docker service starts on boot by default. 
```
service docker status
# or,
systemctl status docker
```
Note: "Loaded: loaded (/lib/systemd/system/docker.service; **enabled**; vendor preset: enabled)"

## 5. Docker commands
### 5.1. Try some basic docker
```
docker
docker --help
docker info

docker version
docker --version

docker images
docker ps
```

### 5.2. Run a Hello World application -- To verify that the Docker Engine installation is successful or not
```
docker run hello-world
    # The "hello-world:latest" docker image is pulled from Docker Hub and exectued in Docker container and produced the output "Hello from Docker!".
    
docker ps -a
```

---

Thank you for Watching, Liking and Sharing! 🙌 ✔ 👌 😍 😊 🙏 

https://www.youtube.com/@Easy-Techie and https://www.linkedin.com/in/santosh-kumar-arjunan/
---
