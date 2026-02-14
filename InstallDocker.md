# Command to Install Docker in Ubuntu
## Update package index
```
sudo apt update
```
## Install prerequisites
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
## Add Docker's official GPG key
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
## Add Docker repository
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
## Update package index again
```
sudo apt update
```
## Install Docker
```
sudo apt install docker-ce docker-ce-cli containerd.io
```
## Start and enable Docker service
```
sudo systemctl start docker
sudo systemctl enable docker
```
## Add your user to docker group (optional, to run docker without sudo)
```
sudo usermod -aG docker $USER
```
Close the connection ssh and try again or restart the instance ec2. Example replace $USER=jenkins
