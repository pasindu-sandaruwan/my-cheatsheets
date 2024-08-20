## Configuring Chrome in WSL for Cypress GUI testing

Ref : [https://www.gregbrisebois.com/posts/chromedriver-in-wsl2/](https://www.gregbrisebois.com/posts/chromedriver-in-wsl2/)

1. Installing chrome in ubuntu
```
sudo apt-get update
```

```
sudo apt-get install -y curl unzip xvfb libxi6 libgconf-2-4
```

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

```
sudo apt install ./google-chrome-stable_current_amd64.deb
```
---

2. Installing the Chrome driver
```
wget https://chromedriver.storage.googleapis.com/86.0.4240.22/chromedriver_linux64.zip
```

```
unzip chromedriver_linux64.zip
```

```
sudo mv chromedriver /usr/bin/chromedriver
```

```
sudo chown root:root /usr/bin/chromedriver
```

```
sudo chmod +x /usr/bin/chromedriver
```

---

3. Check version to verify the installation

```
chromedriver --version
```




