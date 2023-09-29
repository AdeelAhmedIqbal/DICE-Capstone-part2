# DICE-Capstone-part2
## Creating VMs, Infra as a Code (IaC)
### 1 - Creating VPC
Creating IPv4 CIDR of 10.0.0.0/28 for our new VPC (Adeel-VPC). We have decided to go with this CIDR because based on our project requirement we will have 2 total main hosts (client & server). Moreover, as we will have 1 subnet based on our requirement, 5 IPs will be reserved by AWS. And the rest of remaining IPs will be kept or can be used later for future when instances auto-scale or increases, and it can also later be utilized when we need more subnets.

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/b3dc56d2-864c-44d7-8e41-a01af43dcb64)

New VPC (Adeel-VPC) successfully created
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/3461cf3e-a57f-4ce6-ab74-9385ab6e9d6a)

### 2 - Creating Subnet 
Now we will create a subnet (Adeel-subnet1) in **eu-north-1a** availability zone. The IPv4 CIDR block for this subnet is **10.0.0.0/28** (which means total 16 hosts / IPs in this subnet).
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/cb2ffc88-73aa-4ed7-baaf-b9e307d1e67f)

### 2.1 - Auto-assign IP setting for subnets:
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/bd783f9b-5c9b-4c07-a887-5a7eb8e8eb44)

### 3 - Creating Internet Gateway
Internet Gateway (Adeel-igw) was created so that our VPC (Adeel-VPC) can be connected to the internet.
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/76ab6c22-0476-4778-9e8b-57c91ad2ee3a)

Attaching Internet Gateway with VPC (Adeel-VPC):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/382ff3bb-90e2-4b88-bf18-d8fa8bd17acb)

### 4 - Creating Routing Table
Creating Route table (Adeel-rt) in order to specify how packets are forwarded between the subnets within our created VPC (Adeel-VPC) and the internet.

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/b6a9d517-22df-4234-b758-f428d7fbca00)

**Associating the created route table (Adeel-rt) with Adeel-subnet**

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/19395b54-7fdc-4b7e-bda7-4a0ed52e7f48)

**Adding route to routing table so that all traffic will be allowed to access through internet gateway.**

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/e3b98c0e-444e-4312-b233-b9278099437c)

## 5 - Creating EC2 Instances
### 5.1 - Server Instance

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/6a5200da-7786-4efb-b7f4-359b7dacfa2e)

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/99ffe30e-2d4a-421c-9ff7-669387e701fb)

### 5.2 - Client Instance 
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/504bec67-07b3-448a-b85d-8e3b70eb335d)

### 5.3 - Connecting instances using putty software:
Connecting to EC2 instances (DICE-EC2-Server and DICE-EC2-Client) through SSH protocol by using putty software/client.

**Server:**

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/cb7a1e14-5e54-4d5f-b0b0-6351c8b15452**)

**Client:**

![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/9ba9c6a9-449f-4d87-b84a-ab6a595a0174)

**5.4 - Checking the connectivity between both instances:**

Pinging from server instance (ip:172.31.27.46) to client instance (ip:172.31.20.105):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/c01cc18a-7a30-4d8b-870f-b01af74053ba)

## 6 - Initializing the instance configuration for the server instance:
### 6.1 - Cloning the server directory from github:
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/233f0295-cec4-4071-978a-a22b2866d72a)

### 6.2 - Install Docker and Docker-compose
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/c5934c6a-ea43-4f6e-9da1-20d7eaec3bdc)

### 6.3 - Creating network “mynetwork” on EC2 instance (DICE-EC2-Server):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/4be46fe7-6b49-4e5c-8695-f612ca556847)

### 6.4 - Using Docker Compose to create and run the server container on EC2 instance (DICE-EC2-Server):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/65449a57-39c6-4c11-821f-4f45b5894e6a)

## 7 - Initializing the instance configuration for the client instance:
### 7.1 - Cloning the server directory from github:
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/866effc1-4664-4255-aca5-1902e9bcb272)

### 7.2 - Install Docker and Docker-compose
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/638a7189-3cfd-408d-9288-d3c867e91e0f)

### 7.3 - Creating network “mynetwork” on EC2 instance (DICE-EC2-Client):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/24016da9-4c38-43cc-94b4-88dfa9e7b9ce)

### 7.4 Changing client application python file (Updating IP address/Hostname and adding wait function to keep the container running):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/9d4b2d0a-ecce-42c3-a66c-cd9e9e9ecc3f)


### 7.4 - Using Docker Compose to create and run the client container on EC2 instance (DICE-EC2-Client):
![image](https://github.com/AdeelAhmedIqbal/DICE-Capstone-part2/assets/62285793/bb7f40a6-d3ac-41d3-a05c-ad9ebb7cc439)









