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
4. Created python script to generate dummy data for analysis.
  4.1 Generated dimensions and fact csv files.
6. Created S3 bucket.
   4.1 Created folders which are representing every table of logical schema. This is needed for crawler to create physical schema. One S3 bucket folder == table.
   4.2 Uploaded data to S3.
7. Created AWS Glue crawler to create metadata for physical model:
   5.1 Added cliffier to highlight separator in CSVs as "|".
   5.2 Created IAM role for crawler.
   5.3 Created dev database for crawler.
   5.4 Ran crawler. 14 new tables created in Glue Database.
8. Validated schemas and data population using Athena.
9. Loaded data to Redshift bronze layer using CREATE EXTERNAL SCHEMA FROM DATA CATALOG.
   8.1 Validate data availability.
### DBT
10. Install dbt-redshift package on local machine. And inititialize a dbt project and establish a connection to Redshift.
    10.1 dbt init - initializes dbt project
    10.2 dbt debug - helps to identify issues with connection
    10.3 Noticed ubuntu machine didn't connected to the database. Went back to 3.1 and added ubuntu IP to security VPC group. 
