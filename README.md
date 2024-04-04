USING AWS FREE TIER (one year for free for multiple AWS services including Elastic Beanstalk/ AWS RDS):

First created, ran the scripts of MySQL db (using MySQL workbench interface) locally with the Spring MVC app.

Then migration to AWS RDS: 
1) Create an RDS instance using MySQL with all configuration (creating new VPC security group with inbound connection rules)
2) Test databse connection with mysql workbench
3) Run sql scripts to create table and load sample data in AWS

Creating Elastic Beanstalk instance in classic way (with all details in application-prod.properties from the SpringBoot app):
1) Updating application-prod.properties: SERVER_PORT=5000 / SPRING_PROFILES_ACTIVE= prod
2) Package the MVC app with database in Maven to get the JAR file
3) Upload JAR into AWS Beanstalk

Then, updating Elastic Beanstalk by providing confidential info from application-prod.properties in AWS instead (Use environment properties/ environment variables in AWS)

Finally, updating Elastic Beanstalk instance using AWS Systems Manager Parameter Store: storing config data as plain text or encrypted data/ data accessing security control/centralized solution

1) Create parameters in AWS parameter store (vs AWS Secrets manager which is a paid service)
2) Attach policy to AWS role  (amazonSSMReadOnlyAccess)
3) update applicaiton-prod.properties in Spring boot app
4) Update Maven pom.xml
5) Package the Spring boot app with Maven
6) Update AWS environment properties
7) Upload the Spring Boot JAR file to Elastic Beanstalk

Lastly: Amazon Route 53 to customize the public name domain (Followed only the different steps for testing purpose and not implemented it as the service is not free in AWS free tier)
