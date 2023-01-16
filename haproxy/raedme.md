https://linuxhint.com/how-to-install-and-configure-haproxy-load-balancer-in-linux/
---
# s1:- (node1)
  * sudo vi /etc/hosts
      # HAproxy 192.168.72.157
  * sudo apt update
  * sudo systemctl enable apache2
  * sudo systemctl start apache2
  * echo "<H1>Hello! This is webserver1: 172.31.1.212 </H1>" | sudo tee /var/www/html/index.html
  * sudo ufw allow 80/tcp 
---
# s2:- (node2)
  * sudo apt update
     * sudo vi /etc/hosts
        # HAproxy 192.168.72.157
  * sudo systemctl enable apache2
  * sudo systemctl start apache2
  * echo "<H1>Hello! This is webserver2: 172.31.42.235 </H1>" | sudo tee /var/www/html/index.html
  * sudo ufw allow 80/tcp

---
# ha proxy:- (node3)

* sudo vi /etc/hosts
    HAproxy 172.31.13.224
    web-server1 172.31.1.212
    web-server2 172.31.42.235
* sudo apt-get update
* sudo apt install haproxy
* haproxy -v
*  sudo vi /etc/haproxy/haproxy.cfg
* frontend web-frontend
   bind 172.31.13.224:80
   mode http
   default_backend web-backend
backend web-backend
   balance roundrobin
   server web-server1 172.31.1.212:80 check
   server web-server2 172.31.42.235:80 check
listen stats
bind 172.31.13.224:8080
mode http
option forwardfor
option httpclose
stats enable
stats show-legends
stats refresh 5s
stats uri /stats
stats realm Haproxy\ Statistics
stats auth ubuntu:ubuntu            #Login User and Password for the monitoring
stats admin if TRUE
default_backend web-backend
* haproxy -c -f /etc/haproxy/haproxy.cfg
* sudo systemctl restart haproxy.service
* sudo systemctl status haproxy.service


ansible facts:-
# ansible -i hosts -m setup all
haproxy:-
# "ansible_hostname": "ip-172-31-13-224"
node1:-
# "ansible_hostname": "ip-172-31-1-212"

node2:-
#  "ansible_hostname": "ip-172-31-42-235"

# docker container start container_name