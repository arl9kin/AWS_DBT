# AWS_DBT project
## Use Case
Simple Bank operations with customers transactions loans and investments.

## Logical Schema
![alt text](https://github.com/arl9kin/AWS_DBT/blob/main/content/logical_view.drawio.png?raw=true)

## Steps
1. Created VPC
2. Created Redshift cluster
   2.1 Set default IAM group
   2.2 Defined cluster subnet group, attached to VPC created above
3. Security VPC group:
  3.1 Added a new inbound and outbound rule to the security VPC group, notably: Redshift access and my IP address.
