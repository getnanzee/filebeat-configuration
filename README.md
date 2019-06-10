# ELK

Filebeat configuration to enable application logging on elasticsearch..

Steps:

Switch to root privileges

  sudo su

###### Step 1: Filebeat Installation:

Install filebeat module on source machine:
  
    rpm:
    curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.1.1-x86_64.rpm
    sudo rpm -vi filebeat-7.1.1-x86_64.rpm

    deb:
    curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.1.1-amd64.deb
    sudo dpkg -i filebeat-7.1.1-amd64.deb

    linux:
    curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.1.1-linux-x86_64.tar.gz
    tar xzvf filebeat-7.1.1-linux-x86_64.tar.gz
  
###### Step 2: Filebeat configuration:
 
To configure filebeat, you need to edit the filebeat configuration which is located in /etc/filebeat:
 
 cd /etc/filebeat
 vi filebeat.yml
   
 The important sections in the filebeat.yml file are listed below:
 - filebeat.inputs
 - setup.template
 - setup.kibana
 - output.elasticsearch
 - processors
      
###### Step 3: Refer to the sample config file attach in the repository
  
  
###### Step 4: Once the configurations have been saved as per the sample configuration, start the filebeat service
  
    systemctl start filebeat
    systemctl enable filebeat
    systemctl status filebeat
  
###### Step 5: Once the sevice status is active, goto you kibana dashboard and click on Discover link in the left panel


###### Step 6: Setup the index pattern in kibana using the index name mentioned in elasticsearch, select @timestamp in Time Filter Field


###### Step 7: You should now be able to see the logs from your app machine is your kibana console, click on Discover to view the logs for further analysis
