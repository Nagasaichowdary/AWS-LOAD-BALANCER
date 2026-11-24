# AWS-LOAD-BALANCER
# EX 6B AWS LOAD BALANCER
## NAME: POPURI ADITYA NAGA SAI
## REG NUMBER: 212223110036
## AIM
To use Elastic Load Balancing (ELB) and Auto Scaling services to load balance and automatically scale an AWS infrastructure.

## ALGORITHM
### Step 1: Create an AMI for Auto Scaling
Open the EC2 console, confirm that Web Server 1 is running (2/2 status checks passed), select the instance, and choose Actions → Image and templates → Create image. Name it "WebServerAMI" and create it. This AMI will be used to launch identical instances later.

### Step 2: Create a Target Group and Load Balancer
Create a Target Group named "LabGroup" (type: Instances, VPC: Lab VPC) without registering targets yet. Then create an Application Load Balancer named "LabELB" under Lab VPC, mapped to Public Subnet 1 and Public Subnet 2, using the Web Security Group, with the HTTP:80 listener forwarding to LabGroup.

### Step 3: Create a Launch Template and Auto Scaling Group
Create a Launch Template named "LabConfig" using the WebServerAMI, instance type t2.micro, key pair "vockey", the Web Security Group, and Detailed CloudWatch monitoring enabled. Using this template, create an Auto Scaling group named "Lab Auto Scaling Group" attached to Private Subnet 1 and Private Subnet 2, linked to the LabGroup target group, with desired/minimum/maximum capacity of 2/2/6 and a target tracking scaling policy set to maintain 60% average CPU utilization.

### Step 4: Verify Load Balancing
Confirm that two new "Lab Instance" EC2 instances were launched by Auto Scaling and that both show a "healthy" status in the LabGroup target group. Copy the Load Balancer's DNS name and open it in a browser to confirm the application is being served correctly through the load balancer.

### Step 5: Test Auto Scaling
Lower the scaling policy's target CPU value to 50% to make scaling trigger sooner, then use the application's "Load Test" feature to generate high CPU load across the instances. Monitor the CloudWatch alarms (AlarmLow/AlarmHigh) until AlarmHigh enters the "In alarm" state, then verify in the EC2 console that additional instances were automatically launched to handle the load.
### Step 6: Terminate the Original Web Server
Select Web Server 1 (the original instance used to create the AMI) and terminate it, since it is no longer needed once the Auto Scaling group is managing instances independently.

## OUTPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/615959b3-48b4-40da-be65-4c78fb601532" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/02fbb617-74b1-4248-99fa-52119200525d" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/73409ae4-b0f1-4db5-aeca-d893d315cc55" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5384ac62-ef92-4581-a0e3-dbcaede12479" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/50b35d88-f0fd-4951-93b1-870aaaf5ff23" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2a58b9be-d2e2-4732-8af6-87d52a15de9c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b8351567-2ce0-4bf8-9224-b4b0d92975e4" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b358529e-5822-4d63-8531-9ca811d8e0ab" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/19a34499-57a3-40d0-9b22-f3aded7c9df4" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1e5482bf-c53a-42d1-bb72-37c3cd640f97" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/15f1bfed-1073-482a-b333-9ea28136b2af" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e7fcf6d0-dc06-4b08-9ae1-1cfad51146cf" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9ed7dc9a-0e36-4dc4-9866-b4b8ee798bef" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1f7192c6-bf3a-4049-8378-9d76ec0cdd01" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6a0d5328-e3ed-407d-a6d1-2c045aef4bd2" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7bd1998e-827c-4843-bed1-c630b4645029" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c0ba7319-e8c5-4949-8d38-5c278be30645" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0d5870d2-647a-4168-8fb2-f8948acf218f" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/84d70767-fb6d-484f-bcd8-bd7d71aed3df" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ca4ea4a6-a58f-4662-8d6e-0deadebd9847" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ef1a3b6e-5389-4523-a96d-e6c28a565497" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c33219ff-24ce-4957-b5b4-2bb72264548d" />


## RESULT
Thus, an AMI was created from a running EC2 instance, a Load Balancer was configured to distribute traffic across multiple instances, an Auto Scaling group was set up with a target tracking scaling policy, and the infrastructure was verified to automatically scale out under increased load using CloudWatch alarms.
