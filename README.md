Adonis Research & Technology Ltd
-----------------------------------------------------------------------------

sudo apt update

sudo passwd root

su - root

apt install curl

curl -fsSL https://download.docker.com/linux/ubuntu/gpg |  gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg


echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" |  tee /etc/apt/sources.list.d/docker.list > /dev/null

apt update

apt-cache policy docker-ce

apt install docker-ce

systemctl status docker

docker build -t ocserv https://github.com/iw4p/OpenConnect-Cisco-AnyConnect-VPN-Server-OneKey-ocserv.git

docker run --name ocserv --privileged -p 443:443 -p 443:443/udp -d ocserv

#---> Change the Specific port : docker run --name ocserv --privileged -p 992:443 -p 992:443/udp -d ocserv

#---> Add User:
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd test

#---> Show Users with Hash Passwords:
docker exec -ti ocserv cat /etc/ocserv/ocpasswd

#---> Change Passwords:
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd USERNAME

#---> Keys:{-d=Delete , -l=Lock , -u=UnLock}
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -d USERNAME
