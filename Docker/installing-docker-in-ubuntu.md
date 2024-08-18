## Installing docker in Ubuntu 22

1. Package update
```
sudo apt-get update
```

2. Install the necessary packages that allow apt to use repositories over HTTPS
```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

3. Add Docker's GPG key to ensure the software you download is authentic
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. Add the Docker repository to APT sources
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Update the package database again to include Docker's packages
```
sudo apt-get update
```

6. Install Docker CE (Community Edition)
```
sudo apt-get install docker-ce
```

7. Check Docker version installing
```
sudo docker --version
```

8. To run Docker commands without sudo, you can add your user to the docker group
```
sudo usermod -aG docker ${USER}
```

## Start the Docker 

1. Start Docker
```
sudo systemctl start docker
```

2. Enable Docker to start at boot
```
sudo systemctl enable docker
```

3. Check Docker service status
```
sudo systemctl status docker
```


