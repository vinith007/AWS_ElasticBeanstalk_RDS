This is application running in local inorder to run the application in aws uncomment the lines and comment the lines port and url which is local.

To run the application in aws <br>
1)Create the default VPC first <br>
2)Provision RDS with MySql <br>
3)Provision Elastic beanstalk <br>
4)deploy the jar of our application(To generate the Jar run build or maven install it will be target folder)


**Detailed Instructions on how to provision resources on AWS and run application <br>**

## Creating database in AWS

1. Search for RDS -> databases -> create databases
2. I have chosen MySql for my project
3. Select version of MySql which you want to use
4. Select free tier if you want to learn or you can choose any option in two
5. Give the identifier to your db instance
6. Create Username and Password
7. In connectivity you must setup the VPC if you want or else you can use the default VPC
8. Next select the subnets
9. Set whether you want to give public access to the database or not
10. To add more security for the database you can create security groups when you create VPC and add those security groups
11. Mention the database name which will be our schema name
12. Click on create database
13. In the security group which we gave above double check the inbound rules whether it has MYSQL/Aurora, TCP, Anywhere(0.0.0/0)
14. 

## Connecting Application to AWS RDS and testing locally

1. Once database is created click on database copy the endpoint
2. In the application.properties file in the url replace {aws.rds.host} with the copied endpoint
3. Change username and password in application.properties if you gave other than root credentials
4. Try running application on local and test the CRUD operations
5. To view data you can install MYSQL workbench and give the hostname, username and password that should establish the connection
6. If it is successful run query to view the data from the table


## Deploy Microservice on AWS ElasticBeanStalk



1. Create jar file of the application mvn install will create that jar for us
2. Go to AWS console search for ElasticBeanStalk -> create application
3. Give the application name
4. Choose platform as java
5. Select java version
6. Click on Configure more option -> database -> edit database -> give username and password of the database which we created above(Verify database MYSQL and version)
7. Click on create app
8. Once the health is ok the upload the jar file
9. Once deployment is successful you can see the url copy that and start testing in postman with the CRUD operations instead of using localhost
10. Once testing is done you can verify on sql workbench too


# Make sure to terminate resources if you don’t want anymore