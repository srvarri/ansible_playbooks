# https://linuxize.com/post/how-to-install-tomcat-9-on-centos-7/ :- link for service file copy
------------------------------------------------
### `jan5`:-
---------------------------------------------------
vars:-
ansible playbook extra vars command line
---
  * ansible playbook -e "name=ansible" -i invetory vardemo.yaml
--- 
linux:- (bash scripting)
  * echo "hello ${name}"  
--- 
# linuxze install tomcat on centos
centos7 
sudo visudo 
ssh-copy-id devops@ `pvt_ip`
------------------------------------------------
### jan7:-
------------------------------------------------
* Inventory can be written in two formats
  * ini file
  * yaml
```
172.31.24.180
172.31.24.181
dev.internal.qt.com => dns name m/c names
``` 
  * ansible -m setup -i hosts all > ~/facts
    exit
    `sftp devops@ip`
    get facts
    bye
    ssh devops@ip

Adhoc command
-------------
* reboot moudle
*  ansible -i hosts -m debug -a "msg=hello" all
   ansible -i hosts -m debug -a "msg=hello, vars=distribution" all
   ansible -i hosts -m file -a "path=/tmp/foo.conf state=touch" all
   ansible -i hosts -m setup -a "filter=*distribution*" all
   ansible -i hosts -m setup -a "filter=*_os_*" all
   ansible -i hosts -m setup -a "filter=*version*" all
   ansible -i hosts -m setup -a "filter=*ip*" all
   ansible -i hosts -m "stat" -a "path=/opt/tomcat/latest/bin/startup.sh" -b all
--------------
if (os= 'ubuntu') {
   // do somthing for ubuntu
}
if (os= 'centos') {
    // do somthing for centos
} 
// in ansible when  
------------------
* ansible file exists check
  * usage of stats and skipping un-necessary extraction of tomcat
  * As we need to change permission of shell files only when tomcat is  extracted,   using the same condition
  * dont excute same thing in mulitipul times. it is only 
----------------------------------------------------------
### jan8th:-
-------------
Tomcat Playbook optimization:
  * sudo systemctl status tomcat.service
  * cd /var/log
  * ls 
  * sudo systemctl daemon-reload 
  * sudo systemctl restart tomcat.service 
  * sudo systemctl status tomcat.service
-----------------
* `Handlers` :- which dont used evey time
------------------
* The way we copied the same content into two different locations with two different files [Refer Here] for the changes.
  print(1)
  print(2)
  print(3)
  ...
  
  print(10)

  for index in 1..10:
    print(index)
--------------------
`loops` :- 
* for item in 1..10:
      print(item)
  - name: some task 
    debug: 
      msg: "hello {{ item }}"
    loop: 
      - 1
      - 2  
------------------------ 
* Lets summarize the improvements which we have done
  * Using Generic modules like package over `apt` or `yum`
  * Using `variables` to parametrize gives us options to set host and group level values
  * conditionally execute tasks based on `facts`
  * `use handlers for automating steps` which need `not execute every time` and `they are  required based on some changes`
  * `use loops` rather than `copy paste of modules`. 

