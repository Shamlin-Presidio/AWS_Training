# VPC

Summarised Idea from ChatGPT:
--------------------------------
| Subnet Type | Purpose                         | Internet Access | Use Cases                            |
| ----------- | ------------------------------- | --------------- | ------------------------------------ |
| Public      | Internet-facing services        | ✅ Yes           | Nginx for public users               |
| Private     | Internal services with internet | ✅ Yes (via NAT) | App servers, Nginx in private subnet |
| Isolated    | Internal only, AWS access only  | 🚫 No           | DBs, internal processing, Lambda     |


Name	              CIDR	       
PublicSubnet-A	    10.0.0.0/24	
PrivateSubnet-A	    10.0.1.0/24	
IsolatedSubnet-A	  10.0.2.0/24	
PublicSubnet-B	    10.0.10.0/24	
PrivateSubnet-B	    10.0.11.0/24	
IsolatedSubnet-B	  10.0.12.0/24	
