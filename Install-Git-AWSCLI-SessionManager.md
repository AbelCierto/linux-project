# Setup: Git, AWS CLI v2, and Session Manager Plugin

This guide explains how to install the required tools on **Ubuntu/Debian Linux** systems.

---

## 1. Install Git
```bash
sudo apt-get update -y
sudo apt-get install -y git
git --version
```


## 2. Install AWS CLI v2

### Install required dependency
```
sudo apt-get update -y
sudo apt-get install -y unzip curl
```

### Download and install AWS CLI v2
```
curl -fsSL "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip -o awscliv2.zip
sudo ./aws/install --update
```

### Verify installation
```
aws --version
```

# 3. Install Session Manager Plugin

### Download the plugin package
```
curl -fsSL "https://s3.amazonaws.com/session-manager-downloads/plugin/latest/ubuntu_64bit/session-manager-plugin.deb" -o "session-manager-plugin.deb"
```

### Install the package
```
sudo dpkg -i session-manager-plugin.deb
```
### Verify installation
```
session-manager-plugin --version
```