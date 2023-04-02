# Ansible-scripting--complete-vpc-java-web-stack-on-the-vpc-and-deploying-using-jenkins

Step 1: Creating a VPC with the following resources.
•	3 public subnets

•	3 private subnets

•	internet gateway and public subnet routing table

•	nat gateway and allocate elastic Ip address

•	create route table for private subnets
all these details are copied to output_var file

Step 2: Creating a bashion host

•	Create EC2 key pair

•	Store the private key

•	Create security group to allow SSH from my IP address

•	Create bashion host EC2 instance

Step 3: Creating ec2 instance for web stack with tomcat,elastic search, rabbitmq, nginx & ELB
•	Create EC2 key pair

•	Store the private key

•	Create security group for ELB – allow http requests

•	 Create security group for instances – to allow ssh from bashion host and all requests from ELB security group

•	Create following instance in the private subnet with key pair and security group created for instances

	Ngnix

	RabbitMq

	Tomcat

	Memcahed

	MySQL

•	Configure ELB with nginx instance on the public subnet with appropriate listeners

•	Finally create ansible inventory file with all the required details

Step 4: Configure playbooks for all the server instances and integrated jenkins with ansible

•	Setup ansible.cfg with the inventory file created in step 3

•	Write following playbooks:

o	MYSQL – copy db and instantiate mysql server

o	Build – build artifact using maven

o	Memcached – setup and configure Memcached server

o	Nginx – setup and copy nginx properties as template

o	RabbitMQ – setup and instantiate RabbitMQ server

o	Tomcat – setup and deploy artifact generated in tomcat. Configure properties using template

•	Configure /etc/hosts in all servers by logging in as the bashion host

This will setup a entire web application stack on ansible

![image](https://user-images.githubusercontent.com/102613218/229353829-1e8dc025-dfc1-4c61-b24e-53b55939dc8c.png)



Step 5: Write jenkins as a pipeline code to deploy artifact to production using ansible

Perform CI using jenkins and deploy artifact to prod tomcat server using tomcat playbook managed by ansible
![image](https://user-images.githubusercontent.com/102613218/229353987-82954cc9-f19b-4978-9e81-826eb78d65f4.png)

![image](https://user-images.githubusercontent.com/102613218/229353976-6e154eb2-e6a3-454f-9ee7-e286f1700dea.png)

![image](https://user-images.githubusercontent.com/102613218/229353993-4ea3be75-3faa-4ec0-946c-a013b6ad1c17.png)
![image](https://user-images.githubusercontent.com/102613218/229354006-69941e29-1db8-4744-a061-8825921986e1.png)

![image](https://user-images.githubusercontent.com/102613218/229354019-3e670dc4-8f4d-4756-aaba-02eccfc14e86.png)
![image](https://user-images.githubusercontent.com/102613218/229354028-149b3213-bc40-4372-b8f4-af97b0e1ad39.png)
![image](https://user-images.githubusercontent.com/102613218/229354033-9903628c-638a-4375-8c88-eb648a6a5f76.png)
![image](https://user-images.githubusercontent.com/102613218/229354038-03a1fa1c-2105-4e79-ab98-9b470d332351.png)
![image](https://user-images.githubusercontent.com/102613218/229354043-282c1346-ebee-4d71-a674-ccdfd887f02d.png)
![image](https://user-images.githubusercontent.com/102613218/229354049-bc3309c5-909a-49ee-b58f-510e889b44b6.png)
![image](https://user-images.githubusercontent.com/102613218/229354055-96dcca0c-a9e1-477b-a2ad-a7df3092541e.png)

Deployment to production
![image](https://user-images.githubusercontent.com/102613218/229354082-22cca561-cf14-4045-923f-e75aa5caf097.png)
![image](https://user-images.githubusercontent.com/102613218/229354090-b1a796f6-869e-49f3-8b30-a8239eb6fb47.png)
![image](https://user-images.githubusercontent.com/102613218/229354097-6d92ad8d-4370-44a5-98cb-2305f63d1b90.png)






