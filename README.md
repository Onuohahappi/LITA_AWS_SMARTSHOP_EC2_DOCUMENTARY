# LITA_AWS_SMARTSHOP_EC2_DOCUMENTARY
 Smartshop is a mid-sized enterprise that recently expanded their business by launching an online store. They anticipate to increase web traffic due to their marketing awareness and seasonal sales. SmartShop requires a robust and reliable web infrastructure to ensure smooth customer experiences.

 ## Introduction:
 - This project is aimed to build an infrastructure for smartshop and develop a solution that meets SmartShop's requirements by leveraging AWS services such as EC2,Virtual Private Cloud (VPC), and Identity and Access Management (IAM) to meet Smartshop's requirement to increase sales and avaoid traffic.

 ## First, VPC setup... 
 #### Virtual Private Cloud (VPC)
- I created a VPC with the name LITA_project_VPC, with an IPv4 CIDR block of 10.0.0.0/16. Within this VPC, I set up two subnets: PublicSubnet (10.0.1.0/24) for resources that need internet access and PrivateSubnet (10.0.2.0/24) for internal resources.
![vpc's](/VPC_1.png)
![vpc](/VPC.png)

### NACL
- An internet gateway named LITA_project_VPC was created and attached to the public and private subnets with an inbound rule to allow SSH(22) and HTTP(80) from anywhere-IPv4 and outbound rule of All traffic from Anywhere-IPv4 to enable internet access for the public subnet.
![NACL](/Nacl.jpg)

### ROUTE TABLES
- Route tables were configured to manage the traffic flow, allowing the SSH and HTTP to ensure the public subnet routes traffic through the internet gateway with the destination being : 0.0.0.0/0.
![Route Table](/rt.jpg)
![Public Subnet](/Public_subnet.png)
![Private Subnet](/Private_subnet.png)

### SECURITY GROUP
- For security group I allowed inbound HTTP (port 80) from anywhere and SSH (port 22) access from the IP for the web and admin access and attached the Security Group to the EC2 instances.
![Security Group](/sg(7).jpg)
![Security Group](/sgn.jpg)

## IAM ROLE
- There was an already IAM user named LITA_project_IAM with AdministratorAccess to manage the AWS account and resources.
![IAM Role](/IAM.png)

## Launching the EC2 instance...
### EC2 Instances
- An EC2 instance was launched using the t2.micro instance type and Amazon Linux 2 AMI. The instance was placed in the PublicSubnet of the  LITA_project_VPC and assigned the necessary permissions.
![t2 micro](/t2_micro.png)
![EC2 Instance](/inst(2)n.jpg)
![EC2 Instance](/instn.jpg)
![EC2 Instance](/AMI_Isnt_2.png)
![EC2 Instance](/AMI_Inst.png)

### Keypair for security...
- I also created a key pair login to securely access the EC2 instances. This key pair allows for SSH access without the need for passwords, enhancing security.
![Keypair](/Keypair_2.jpg)

## Apache Installation and Configuration on EC2 Instance...
-I installed an Apache using the key pair I created earlier, and I ensured I have the latest package using the sudo yum update -y, and installed the Apache using the command sudo yum install httpd -y. I connected the EC2 instance via SSH. By installing and configuring Apache on the EC2 instance, I aimed to verify that the instance is running correctly and capable of serving web requests. The successful display of the Apache default welcome page confirms that the web server is operational.
![Apache](/ApacheB.jpg)
![Apache](/Apache.jpg)