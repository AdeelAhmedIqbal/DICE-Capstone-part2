# DICE-Capstone-part2
## Creating VMs, Infra as a Code (IaC)
### Creating VPC
Creating IPv4 CIDR of 10.0.0.0/28 for our new VPC (Adeel-VPC). We have decided to go with this CIDR because based on our project requirement we will have 2 total main hosts (client & server). Moreover, as we will have 1 subnet based on our requirement, 5 IPs will be reserved by AWS. And the rest of remaining IPs will be kept or can be used later for future when instances auto-scale or increases, and it can also later be utilized when we need more subnets.

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/b3dc56d2-864c-44d7-8e41-a01af43dcb64)

New VPC (Adeel-VPC) successfully created
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/3461cf3e-a57f-4ce6-ab74-9385ab6e9d6a)

### Creating Subnet 
Now we will create a subnet (Adeel-subnet1) in **eu-north-1a** availability zone. The IPv4 CIDR block for this subnet is **10.0.0.0/28** (which means total 16 hosts / IPs in this subnet).
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/cb2ffc88-73aa-4ed7-baaf-b9e307d1e67f)

### Auto-assign IP setting for subnets:
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/bd783f9b-5c9b-4c07-a887-5a7eb8e8eb44)

### Creating Internet Gateway
Internet Gateway (Adeel-igw) was created so that our VPC (Adeel-VPC) can be connected to the internet.
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/76ab6c22-0476-4778-9e8b-57c91ad2ee3a)

Attaching Internet Gateway with VPC (Adeel-VPC):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/382ff3bb-90e2-4b88-bf18-d8fa8bd17acb)

### Creating Routing Table
Creating Route table (Adeel-rt) in order to specify how packets are forwarded between the subnets within our created VPC (Adeel-VPC) and the internet.

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/b6a9d517-22df-4234-b758-f428d7fbca00)

**Associating the created route table (Adeel-rt) with Adeel-subnet**

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/19395b54-7fdc-4b7e-bda7-4a0ed52e7f48)

**Adding route to routing table so that all traffic will be allowed to access through internet gateway.**

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/e3b98c0e-444e-4312-b233-b9278099437c)

## Creating EC2 Instances
### Server Instance

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/6a5200da-7786-4efb-b7f4-359b7dacfa2e)

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/99ffe30e-2d4a-421c-9ff7-669387e701fb)

### Client Instance 
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/504bec67-07b3-448a-b85d-8e3b70eb335d)





