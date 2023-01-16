# t2.small
 Update the system. `sudo apt update`
* Step 1: Download the nop using wget.
  * `wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb`
  *  `sudo dpkg -i packages-microsoft-prod.deb`
* Step 2: Install DotNet
  * `sudo apt-get update`
  * `sudo apt-get install -y apt-transport-https aspnetcore-runtime-7.0`
  * dotnet --list-runtimes
* step3: install my_sql 
  * sudo apt-get install mysql-server`
  * sudo /usr/bin/mysql_secure_installation`
# mysql -u root
# ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'Kiran@1234';
# exit
* step : insatll nginx 
  * `sudo apt-get install nginx`
  * `sudo systemctl start nginx`
  * `sudo systemctl status nginx`
  * `sudo vi /etc/nginx/sites-available/default`
* Step 4: Create a folder.      
  * `mkdir /var/www/nopCommerce`
  * `cd /var/www/nopCommerce`
* Step 5: Download the WildFly using wget.
  * `sudo wget https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.0/nopCommerce_4.60.0_NoSource_linux_x64.zip`
  * `sudo apt-get install unzip`
  * `sudo unzip nopCommerce_4.60.0_NoSource_linux_x64.zip`
* Step 6: Create a folder. 
  * `sudo mkdir bin`
  * `sudo mkdir logs`
cd ..
* Provide the following permission: 
  * `sudo chgrp -R www-data nopCommerce/`
  * `sudo chown -R www-data nopCommerce/`
* Step 7: Start & Enable the WildFly service.  
  * `sudo vi /etc/systemd/system/nopCommerce.service`
  * `sudo systemctl start nopCommerce.service`
  * `sudo systemctl status nopCommerce.service`
  * `sudo systemctl restart nginx`

# https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html