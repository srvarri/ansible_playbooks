sudo apt update
sudo apt install openjdk-11-jdk -y
java -version
sudo useradd -m -U -d /opt/tomcat -s /bin/false tomcat
VERSION=10.1.4
wget https://www-eu.apache.org/dist/tomcat/tomcat-10/v${VERSION}/bin/apache-tomcat-${VERSION}.tar.gz -P /tmp
sudo tar -xf /tmp/apache-tomcat-${VERSION}.tar.gz -C /opt/tomcat/
sudo ln -s /opt/tomcat/apache-tomcat-${VERSION} /opt/tomcat/latest
sudo chown -R tomcat: /opt/tomcat
sudo sh -c 'chmod +x /opt/tomcat/latest/bin/*.sh'
sudo nano /etc/systemd/system/tomcat.service
sudo systemctl daemon-reload
sudo systemctl enable --now tomcat
sudo systemctl status tomcat
---
 DOTONT WANT => FIREWALL
CONFIGURING TOMCAT WEB MANAGMENT INTERFACE:
1) TOMCAT-USERS.XML
       USERNAME: admin
	   password: admin_password
2)MANAGERAPP
       ALLOW=".*"
3)HOST MANAGERAPP
       ALLOW=".*"
4)restart
---
# useradd --help
# download tomcat
#10.1.4
name=Ansible
echo "Hello ${name}"
# wget --help
ln -s => sybalic link in windows=> shortcut to the folder
# chown --help	