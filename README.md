# Linux-Commands
Useful Linux Commands 

#### Rerouting ports

```sh
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
```
or 

```sh
iptables -t nat -A OUTPUT -o lo -p tcp --dport 80 -j REDIRECT --to-port 8080
```
>  Useful for redirecting ports i.e 
``` sh
iptables -A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --dport 8080 -j ACCEPT
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
```
then to save config
```sh 
 sudo apt-get install iptables-persistent
```
or if configured 
```sh 
 sudo dpkg-reconfigure iptables-persistent
```
then
```sh
sudo iptables-save | sudo tee /etc/iptables/rules.v4
sudo ip6tables-save | sudo tee /etc/iptables/rules.v6 
```

#### Active ports
```sh 
netstat -ntlp | grep LISTEN
```
> Useful to check ports actively open 

## Other Useful Commands 
Other useful commands

## Docker
Useful docker commands

#### Installing Docker CLI 
```sh 
sudo apt-get install      ca-certificates      curl      gnupg      lsb-release
```
```sh 
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
```
```sh 
 $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```sh 
sudo apt-get update
```
```sh 
sudo apt-get update  sudo apt-get install docker-ce docker-ce-cli containerd.io
```
```sh 
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
> Useful to install docker for unbuntu

### Docker pull 
```sh 
docker pull [repository]/[name]:[tag] 
```
> Useful for pulling public repositories off docker hub


### Docker run 
```sh 
docker run -p 8080:[port] [repository]/[name]:[tag]
```
> Useful for running  docker at specific ports. **Note:** prefix with `screen`cmd to run after ssh connection closed

### Docker running containers
```sh 
docker ps
```
> Useful for checking running containers 

### Docker `stop` running containers
```sh 
docker stop [repository]/[name]:[tag]
```
> Useful to stop running containers
