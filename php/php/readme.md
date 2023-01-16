sudo apt update
sudo apt install apache2 -y
sudo apt install php libapache2-mod-php php-mysql -y
# create a file in the path /var/www/html/info.php with content
# <?php phpinfo( ); ?>
sudo systemctl enable apache2
sudo systemctl start apache2
# https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04

<?php phpinfo(); ?>

# sudo vi info.php
#  <?php phpinfo(); ?>
------
centos:-


-------------
yaml format:-
# ansible-playbook -i hosts.yaml php.yanl
---------
