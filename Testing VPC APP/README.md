# Testing for VPC to Working In AWS

## Step 1: App EC2 Instance Launched In Public Subnet  
 
 - Launch an EC2 instance from previous working app ami in the public subnet.  Configure to launch in the VPC created with relevant network configurations as shown below.
 
![image](https://user-images.githubusercontent.com/97620055/187737935-8446aaf8-8eb8-41e3-877f-776fbb0755f8.png)


## Step 2: Security group config for app instance.
  
    - Define the security inbound rules as below (outbound set as default to all): 
    
    ![image](https://user-images.githubusercontent.com/97620055/187739510-6d5c7a68-3c80-49cb-8c82-58f25e7005c5.png)

## Step 3: Database Instance Launched In Private Subnet
  
  - Launchd DB instance with ami but with vpc network settings as below:
  
  ![image](https://user-images.githubusercontent.com/97620055/187746583-b5e51eb7-f4f0-462b-a8d5-5a8084985436.png)

## Step 4: Security group configuration for DB instance.

 - Define rules so access of DN can only be made from app to db and public subnet to db.  See Below: 
  
![image](https://user-images.githubusercontent.com/97620055/187739716-6ae8e3c3-383d-4198-9245-1714e2b27e62.png)


## Step 3: Environmental Setup In App

  - SSH into the APP instance and run the following commands in order:
  * `sudo echo export DB_HOST="mongodb://Private-IPV4-DB:27017/posts" >> ~/.bashrc` ( Connects to mongodb with given ip that connects to posts)
  * `source ~/.bashrc` (need to source file to reload new information)
  * `printenv DB_HOST` (check environment has been made persistent)
  
 ## Step 4: Stop & Relaunch NPM with Data Being Seeded
 
 1. Stop pre-existing NPM service running using commands as follows: 
     * `sudo systemctl disable npm.service`
     * `sudo systemctl stop npm.service` / `sudo systemctl kill npm.service`
 
 2. Data Extraction from Seeds Folder
     * In seeds folder, `node seed.js`
 3. Restart App from App folder
     * Start app > `npm start`
    
    
    


  
