---
   * sudo apt update
   * sudo apt install openjdk-11-jdk -y 
   * link:-  https://updates.jenkins.io/download/war/
   * wget https://updates.jenkins.io/download/war/
   $  `https://updates.jenkins.io/download/war/2.384/jenkins.war` 
   $ java  -jar jenkins.war
   * sudo vi /etc/systemd/system/jenkins.service
   * sudo systemctl restart jenkins.service
   * sudo systemctl status jenkins.service
---
[Unit]
Description=jenkins java application
[Service]
User=devops
# The configuration file application.properties should be here:

#change this to your workspace
WorkingDirectory=/home/devops/

#path to executable.
#executable is a bash script which calls jar file
ExecStart=/usr/bin/java -jar jenkins.war

SuccessExitStatus=143
TimeoutStopSec=10
Restart=on-failure
RestartSec=5

[Install]
WantedBy=multi-user.target


