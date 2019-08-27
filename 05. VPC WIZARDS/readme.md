# 05. VPC WIZARDS.

### Virtual Private Cloud

VPC is a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.

### Internet Gateway

**Internet Gateway** is a VPC component that allows communication between instances in your VPC and the internet

### Route Table

A **Route table** contains a set of rules, called routes, that are used to determine where network traffic is directed.

### Route

Specifies a route in a **Route table** within a VPC.

### Subnet

A part of VPC with specified IP addresses.

### Public Subnet

A subnet with access to the internet

### Private Subnet

A subnet without access to the internet

### Nat Gateway

Enable instances in a private subnet to connect to the internet or other AWS services, but prevent the internet from initiating a connection with those instances.

### Elastic IP

IP address associated with your AWS account which could be easily assigned to any instance in your account.

## LAB

1. Go to **VPC** web console.
    > make sure you are in eu-west-1 (Ireland) region.
2. Launch VPC Wizard
3. Select **VPC with Public and Private Subnets**.
4. Review all the options.
5. Try to create a VPC.
