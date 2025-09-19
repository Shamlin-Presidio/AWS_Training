# Summart:

Summarised Idea from ChatGPT:
--------------------------------
| Subnet Type | Purpose                         | Internet Access | Use Cases  (I wanted to know this    |
| ----------- | ------------------------------- | --------------- | ------------------------------------ |
| Public      | Internet-facing services        | ✅ Yes           | Nginx for public users               |
| Private     | Internal services with internet | ✅ Yes (via NAT) | App servers, Nginx in private subnet |
| Isolated    | Internal only, AWS access only  | 🚫 No           | DBs, internal processing, Lambda     |

Isolated subnet and its connections were the only difference from the course
In the course, he disconnected the Private instance as Bastion from NAT and then connected it using Private link to dynammoDB

# VPC
|Name	              |CIDR	       |
|-------------------|------------|
|PublicSubnet-A	    |10.0.0.0/24 |
|PrivateSubnet-A	  |10.0.1.0/24 |
|IsolatedSubnet-A	  |10.0.2.0/24 |
|PublicSubnet-B	    |10.0.10.0/24|	
|PrivateSubnet-B	  |10.0.11.0/24|	
|IsolatedSubnet-B	  |10.0.12.0/24|	


I created and attached a Gateway to VPC
and updated this in route table:

`0.0.0.0/0 → Internet Gateway`

## NAT instance, then changed to NAT Gateway 


| Subnet   | Route Table Target   |
| -------- | -------------------- |
| Public   | `0.0.0.0/0 → IGW`    |
| Private  | `0.0.0.0/0 → NAT GW` |
| Isolated | No internet route    |


Intances and Nginx servers were created using the above VPC and subnet by loging into each instance in private subnet

# Isolated Subnet Access to AWS Services (like S3)

This was primaruly through the VPC Gateways and then updating the table in the subnet



# Connecting two private subnets was through VPC Peering connection between them (update route table)
