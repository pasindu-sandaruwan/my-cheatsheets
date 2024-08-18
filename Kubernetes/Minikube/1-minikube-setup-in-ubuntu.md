### Setup and installation of Minikube in Ubuntu22

- Pre-requisits:
    - [Installing Docker in Ubuntu](https://github.com/pasindu-sandaruwan/my-cheatsheets/blob/main/Docker/1-installing-docker-in-ubuntu.md)
 
1. Instal Minikube
Ref: [Official Minikube Documentation](https://minikube.sigs.k8s.io/)

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
```
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

2. Start Minikube
```
minikube start
```

---
> [!CAUTION]
> If the following error is occured when starting Minikube: 
```ubuntu@ip-172-31-27-141:~$ minikube start
😄  minikube v1.33.1 on Ubuntu 24.04
👎  Unable to pick a default driver. Here is what was considered, in preference order:
    ▪ docker: Not healthy: "docker version --format {{.Server.Os}}-{{.Server.Version}}:{{.Server.Platform.Name}}" exit status 1: permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.46/version": dial unix /var/run/docker.sock: connect: permission denied
    ▪ docker: Suggestion: Add your user to the 'docker' group: 'sudo usermod -aG docker $USER && newgrp docker' <https://docs.docker.com/engine/install/linux-postinstall/>
💡  Alternatively you could install one of these drivers:
    ▪ kvm2: Not installed: exec: "virsh": executable file not found in $PATH
    ▪ podman: Not installed: exec: "podman": executable file not found in $PATH
    ▪ qemu2: Not installed: exec: "qemu-system-x86_64": executable file not found in $PATH
    ▪ virtualbox: Not installed: unable to find VBoxManage in $PATH
```

- Add your user to the Docker group
```
sudo usermod -aG docker $USER
```

- Refresh group membership
```
newgrp docker
```

- Verify docker permissions by listing down the docker containers
```
docker ps
```

- Start the minikube again to verify the starting
```
minikube start
```
