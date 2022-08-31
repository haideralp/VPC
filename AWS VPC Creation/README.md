# VPC Setup In AWS 
## Step 1: Creating VPC With CIDR Block In AWS

- The first step to create the diagram model on AWS is to create a VPC. So under **VPC** services. Navigate and create VPC as shown in screenshot below. Specifying name and IPv4 CIDR address. This serves as a postcode address for the VPC within availability zone.  

![image](https://user-images.githubusercontent.com/97620055/187682048-41c78e8d-4c9b-4df0-8c56-14bcc8159e6b.png)

- Once created it will show like this below:

![image](https://user-images.githubusercontent.com/97620055/187682312-ddcaae13-6801-43d3-81b9-0c252d492d1c.png)

## Step 2: Internet Gateway (IG) Creation

- We then create an internet gateway that will serve as a door between VPC and the outside (public) world. See below:

![image](https://user-images.githubusercontent.com/97620055/187682670-8e9ca75f-5ef4-4bc7-adef-03f823d9cafd.png) 

- Once created we then attach IG (install door) to the VPC as below

![image](https://user-images.githubusercontent.com/97620055/187683304-67f21c2a-133e-4978-9319-5d66ddee8e12.png)

- Specify the VPC, in this example searched eng122-haider-vpc --> id is displayed specific to my VPC.

![image](https://user-images.githubusercontent.com/97620055/187683602-76697a72-9a0c-4e61-a473-48b98af951bc.png)

- Once confirmed the status will change from detached to attached as below:

![image](https://user-images.githubusercontent.com/97620055/187683772-3fbd319d-f5b2-47fd-b756-3513eb523e3b.png)

## Step 3: Create the Public Subnet  

- We then go on create public subnet with relevant configurations, this is specific to where app/instance is present in the VPC. **10.0.9.0/24** - using CIDR block address for the subnet in my example.  

![image](https://user-images.githubusercontent.com/97620055/187685556-245bbe08-9d19-481d-871e-d2356d7d1293.png)

- If created successfuly, it will show as belwo on AWS management console.

![image](https://user-images.githubusercontent.com/97620055/187685923-8475f71a-ac29-4ff9-a3a0-ea5048354971.png)

## Step 4: Creation of Route Tables (RT) with Subnet Associations

- A route table contains a set of rules, called routes, that determine where network traffic from your subnet or gateway is directed. This is created as shown below:

![image](https://user-images.githubusercontent.com/97620055/187688341-19ae0226-83a6-4804-a86b-c73991219bff.png)


- The relevant subnets are then associated to this route table under the option edit routes. See below:

![image](https://user-images.githubusercontent.com/97620055/187688703-d0ce50ad-7d58-4a68-a784-efc55c90f8e6.png)

- Here you add the IG created with **0.0.0.0/16** - this will allow internet from outside into your VPC region. 

![image](https://user-images.githubusercontent.com/97620055/187689675-cd8f29d6-eb75-44bb-8286-676441c8628c.png)

- In your route table, you go to tab > **subnet association** then > **edit subnet associations**. Select the public and private subnet associations to your table and save. As shown below:

![image](https://user-images.githubusercontent.com/97620055/187690457-1da44288-3993-4249-9fb5-6aec3a3b0ca0.png)

## Step 5. Creating Private Subnet for Database (DB)

- Once the public subnet setup is configured for the app and it has launched with app running and fibonacci page, the private subnet for DB is then configured as follows: 

![image](https://user-images.githubusercontent.com/97620055/187706333-cd921621-f35b-47ba-9401-dc676d0cc62a.png)


## Step 6. Private Subnet Association In Route Table

- A seperate route table is created to serve private subnet region. A route table by default is private, we make it public with 0.0.0.0/0. In this case because DB is within a private subnet we just leave the VPC CIRD Block address. See below:

![image](https://user-images.githubusercontent.com/97620055/187734732-0c24c9a6-3a14-4e47-897a-b241858c0216.png)

- Just a quick overiew of two route tables created for public and private subnet models

![image](https://user-images.githubusercontent.com/97620055/187735125-f3350ddc-751b-4a03-b04c-723300c4b5f5.png)
