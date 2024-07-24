# This is a VPC Module Using AWS


![alt text](images/awsvpc.jpg)

Above  is a Reference Archetecture for the VPC Module.

### step-by-step approach to setting up a VPC with public, private, and database subnets, along with necessary components such as an Internet Gateway, NAT Gateway, and route tables using Terraform.
# VPC Setup with Public, Private, and Database Subnets

## 1. Create VPC
* Enter the VPC name and CIDR block (e.g., 10.0.0.0/16).
## 2. Create an Internet Gateway (IGW)
## 3. Create Subnets
### Public Subnets
* Enter the subnet name (e.g., Public Subnet 1) and CIDR block (e.g., 10.0.1.0/24).
### Private Subnets
* Enter the subnet name (e.g., Private Subnet 1) and CIDR block (e.g., 10.0.2.0/24).
### Database Subnets
* Enter the subnet name (e.g., Database Subnet 1) and CIDR block (e.g., 10.0.3.0/24).
## 4. Allocate an Elastic IP (EIP) for NAT Gateway
## 5. Create NAT Gateway
## 6. Create Route Tables
### Public Route Table
* Add a route to the Internet Gateway (IGW):
   - Destination: `0.0.0.0/0`
   - Target: Internet Gateway 
### Private Route Table
* Add a route to the NAT Gateway:
   - Destination: `0.0.0.0/0`
   - Target: NAT Gateway 
### Database Route Table
## 7. Associate Route Tables with Subnets
* Public Subnets
* Private Subnets
* Database Subnets

### Inputs Required To use This VPC Module
* project_name (Required): User should mention their project name. Type is string.
* environment (Optional): Default value is dev. Type is string.
* common_tags (Required): User should provide their tags related to their project. Type is map.
* vpc_cidr (Optional): Default value is 10.0.0.0/16. Type is string.
* enable_dns_hostnames (Optional): Default value is true. Type is bool.
* vpc_tags (Optional): Default value is empty. Type is map.
* igw_tags (Optional): Default value is empty. Type is map.
* public_subnet_cidrs (Required): User has to provide 2 valid subnet CIDR.
* public_subnet_cidr_tags (Optional): Default value is empty. Type is map.
* private_subnet_cidrs (Required): User has to provide 2 valid subnet CIDR.
* private_subnet_cidr_tags (Optional): Default value is empty. Type is map.
* database_subnet_cidrs (Required): User has to provide 2 valid subnet CIDR.
* database_subnet_cidr_tags (Optional): Default value is empty. Type is map.
* database_subnet_group_tags (Optional): Default value is empty. Type is map.
* nat_gateway_tags (Optional): Default value is empty. Type is map.
* public_route_table_tags (Optional): Default value is empty. Type is map.
* private_route_table_tags (Optional): Default value is empty. Type is map.
* database_route_table_tags (Optional): Default value is empty. Type is map.
* is_peering_required (Optional): Default value is false. Type is bool.
* acceptor_vpc_id (Optional): Default value is empty, default VPC ID would be taken. Type is string.
* vpc_peering_tags (Optional): Default value is empty. Type is map.

### Outputs
* vpc_id: VPC ID
* public_subnet_ids: A list of 2 public subnet IDS created.
* database_subnet_ids: A list of 2 database subnet IDS created.
* private_subnet_ids: A list of 2 private subnet IDS created.
* database_subnet_group_id: A database subnet group ID created.
* igw_id: internte gateway created.
