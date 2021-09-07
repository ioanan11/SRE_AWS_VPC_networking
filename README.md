**Virtual Private Cloud (VPC), CIDR Block** 

![alt text](https://github.com/ioanan11/SRE_AWS_VPC_networking/blob/main/AWS_deployment_networking_security.png)

-What is a VPC?
	Isolated virtual network - it allows us to control virtual environment includinf selection of your own IPs address range, we can create multiple subnets within one VPC with specific network configuration. We can use both IPv4 and IPv6 for most resources, it provides security for your services or instances.

**Subnets**

-What is a subnet?
	
	A segmented piece of a larger network
	The goal is to split a larger network into a smaller, interconnected networks to help minimise traffic or navigate traffic securely

**Internet Gateway**

-What is an internet gateway?
	
	Can transfer communication between an enterprise network (your network) and the internet. 
	It allows access into the VPC.

**Route Tables**
	
	Contains set of rules, called routes, that are used to determine where the network traffic from your subnet or gateway is directed

**Network Access Control list (NACLs)**
	
	NACLs are stateless - we have to explicitly allow inbound and outbound rules - they are an added layer of security to the subnets VPC

There are 4.3 billion IP addresses in the world aprox.


Task: 
1. create a VPC with IPv valid CDIR block
	'10.0.0.0/16', '10.10.0.0/16'
2. create internet gateway
	Attach the IG to your personal VPC
3. create route table
	Edit route and insert your IG 'target'
4. create public subnet
	'10.0.1.0/24'
	Associate public subnet with our RT
5. create public NACLs
	set inbound and outbound rules for this (all ports must be allowed , 22, 3000 etc)
6. create a Security Group for our app

![alt text](https://github.com/ioanan11/SRE_AWS_VPC_networking/blob/main/Screenshot%202021-09-07%20135231.png)


**How to create a VPC**

1. AWS Dashboard -> VPC -> Your VPC -> Create VPC
2. Add name tag, add IPv4 CIDRblock (I will be using 10.103.0.0) 
3. Create VPC
	
**How to create Internet Gateway**

1. AWS Dashboard -> Internet Gateways -> Create Internet gateway
2. Add name tag
3. Create Internet Gateway
4. From Actions select Attach VPC (attach the VPC you have just created) and Attach Internet Gateway

**How to create a Subnet?**

On the left toolbar select Subnet and Create Subnet
	Note: we need 2 subnets, as in the diagram, one private & one public.

For public: 
	-select the VPC created
	-CIDR block IP: 10.103.1.0/24
For private:
	-select the VPC created
	-CIDR block IP: 10.103.2.0/24

**How to create a Route Table?**

1. On the left toolbar select Route Tables
2. Create route table
3. Select Route Table ACtions and Edit Routes
4. Add destination and target. (Target is the internet gateway created earlier, Destination is 0.0.0.0/0)


**How to create NACLs?**
**How to create Security Groups?**
