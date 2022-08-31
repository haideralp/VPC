# Virtual Private Cloud

## Simplistic Diagram Showcasing a VPC Setup 

![image](https://user-images.githubusercontent.com/97620055/187464220-36daa716-ebf7-4319-9ae7-7d01485da43a.png)

## Key Features of VPC:

### Virtual Private Cloud (VPC)

- VPC is a virtual network that resembles a traditional network that you would operate in your own data centre. After creation, you can add subnets. 
    
### Subnets

- A subnet is a range of IP addresses in your VPC. A subnet must reside in a single Availability Zone. After you add subnets, you can deploy AWS resources in your VPC.
### IP addressing

- You can assign IPv4 addresses and IPv6 addresses to your VPCs and subnets. You can also bring your public IPv4 and IPv6 GUA addresses to AWS and allocate them to resources in your VPC, such as EC2 instances, NAT gateways, and Network Load Balancers.
### Routing

- Route tables dictate where traffic from your subnet or gateway is directed. 

### Gateways and endpoints

- A gateway connects your VPC to another network. For example, use an internet gateway to connect your VPC to the internet. Use a VPC endpoint to connect to AWS services privately, without the use of an internet gateway or NAT device.

### Classless Inter-Domain Routing Blocks (CIDR) 

- Classless Inter-Domain Routing (CIDR) blocks are for specifying a range to IP addresses in format of IPv4 or IPv6. For the sake of simplicity I will explain rest of this in format of IPv4 however it is applicable to IPv6.

     **General format for CIDR Blocks: x.y.z.t/p**

- x, y, z and t are numbers from **0 to 255**. Basically, each represents an 8 bit binary number. That's why it is range is up to 255. Combination of this numbers becomes an IPv4 IP address that must be unique to be able to identify a specific instance.

- In case of AWS, **p is a number from 16 to 28**. It represents the number of bits that are inherited from given IP address. For example: 10.0.0.0/16 represents an IP address in following format: 10.0.x.y where x and y are any number from 0 to 255. So, actually it represents a range of IP addresses, starting from 10.0.0.0 to 10.0.255.255.

- However for each CIDR block, AWS prohibits 5 possible IP addresses. Those are the first 4 available addresses and the last available address. In this case:

1. 10.0.0.0: Network address
2. 10.0.0.1: Reserved for VPC router
3. 10.0.0.2: DNS server
4. 10.0.0.3: Reserved for future use
5. 10.0.255.255: Network broadcast

## Creating CIDR Blocks In AWS

## Network Access Control List vs Security Groups


![image](https://user-images.githubusercontent.com/97620055/187655505-1986e454-5a8d-48f3-b66b-200b7b9e5677.png)

## Diagram Showcasing VPC & Subnets Creation


![image](https://user-images.githubusercontent.com/97620055/187668462-6f39dc56-58ae-4e6c-aef7-04d2dd70f19d.png)


### Step 1: Creating VPC With CIDR Block In AWS

- The first step to create the diagram model on AWS is to create a VPC. So under **VPC** services. Navigate and create VPC as shown in screenshot below. Specifying name and IPv4 CIDR address. This serves as a postcode address for the VPC within availability zone.  

![image](https://user-images.githubusercontent.com/97620055/187682048-41c78e8d-4c9b-4df0-8c56-14bcc8159e6b.png)

- Once created it will show like this below:

![image](https://user-images.githubusercontent.com/97620055/187682312-ddcaae13-6801-43d3-81b9-0c252d492d1c.png)

### Step 2: Internet Gateway (IG) Creation

- We then create an internet gateway that will serve as a door between VPC and the outside (public) world. See below:

![image](https://user-images.githubusercontent.com/97620055/187682670-8e9ca75f-5ef4-4bc7-adef-03f823d9cafd.png) 

- Once created we then attach IG (install door) to the VPC as below

![image](https://user-images.githubusercontent.com/97620055/187683304-67f21c2a-133e-4978-9319-5d66ddee8e12.png)

- Specify the VPC, in this example searched eng122-haider-vpc --> id is displayed specific to my VPC.

![image](https://user-images.githubusercontent.com/97620055/187683602-76697a72-9a0c-4e61-a473-48b98af951bc.png)

- Once confirmed the status will change from detached to attached as below:

![image](https://user-images.githubusercontent.com/97620055/187683772-3fbd319d-f5b2-47fd-b756-3513eb523e3b.png)

### Step 3: Create the Public Subnet  

- We then go on create public subnet with relevant configurations, this is specific to where app/instance is present in the VPC. **10.0.9.0/24** - using CIDR block address for the subnet in my example.  

![image](https://user-images.githubusercontent.com/97620055/187685556-245bbe08-9d19-481d-871e-d2356d7d1293.png)

- If created successfuly, it will show as belwo on AWS management console.

![image](https://user-images.githubusercontent.com/97620055/187685923-8475f71a-ac29-4ff9-a3a0-ea5048354971.png)

### Step 4: Creation of Route Tables (RT) with Subnet Associations

- A route table contains a set of rules, called routes, that determine where network traffic from your subnet or gateway is directed. This is created as shown below:



- The relevant subnets are then associated to this route table under the option edit routes. See below:




