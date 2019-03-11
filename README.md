# INSTALL DOCKER 

## Update apt-get 

    $ sudo apt-get update 


## Completely Uninstall old version

    $ dpkg -l | grep -i docker

    $ sudo apt-get purge docker-ce

    $ sudo rm -rf /var/lib/docker

    $ sudo apt-get purge -y docker.io

    $ sudo apt-get autoremove -y --purge docker.io

    $ sudo apt-get autoclean

## Install Docker 

    $ sudo apt-get update 

    $ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

    $ sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add 
    
    $ sudo add-apt-repository \
     "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
     $(lsb_release -cs) \
     stable"

    $ sudo apt-get -f install docker-ce docker-ce-cli containerd.io
    
    $ sudo docker run hello-world


## Custom Proxy for Arcada-Docker

 Working for any PC connect to internet via a proxy server. 

1. Create docker config folder

        $ sudo mkdir /etc/systemd/system/docker.service.d
 
2. Create a new file and open VIM editor

        $ sudo vim /etc/systemd/system/docker.service.d/http-proxy.conf
 
**OR** open this new file with UI (I prefer VIM, if you are not familiar with VIM use this)
 
        $ sudo touch /etc/systemd/system/docker.service.d/http-proxy.conf 
 
        $ sudo gedit /etc/systemd/system/docker.service.d/http-proxy.conf 
 
 add this line to ***http-proxy.conf*** file: 
 
        [Service]
        Environment="HTTP_PROXY=http://proxy.arcada.fi:8080"
        
3. Save file and exit

 
4. Reload Docker Deamon: 
 
        $ sudo systemctl daemon-reload
 
5. Restart docker: 
 
        $ sudo systemctl restart docker
 
6. Verify working Docker: 
 
        $ sudo docker pull hello-world
 
