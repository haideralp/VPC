# Virtual Private Cloud

## Simplistic Diagram Showcasing a VPC Setup 


## Key Features of VPC:

### Virtual private clouds (VPC)
    - A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center. After you create a VPC, you can add subnets.
### Subnets
  - A subnet is a range of IP addresses in your VPC. A subnet must reside in a single Availability Zone. After you add subnets, you can deploy AWS resources in your VPC.
### IP addressing
  - You can assign IPv4 addresses and IPv6 addresses to your VPCs and subnets. You can also bring your public IPv4 and IPv6 GUA addresses to AWS and allocate them to resources in your VPC, such as EC2 instances, NAT gateways, and Network Load Balancers.
### Routing
    - Use route tables to determine where network traffic from your subnet or gateway is directed.

### Gateways and endpoints
    - A gateway connects your VPC to another network. For example, use an internet gateway to connect your VPC to the internet. Use a VPC endpoint to connect to AWS services privately, without the use of an internet gateway or NAT device.
