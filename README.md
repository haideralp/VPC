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

