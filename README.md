# lambda-schedule-start-stop-ec2
stop and start EC2 instances automatically by using Lambda Functions Depends on Tags 

for this task purpose we have to follow below steps
1) create an IAM roles and attach policy 

{ \n
    "Version": "2012-10-17", \n
    "Statement": [\n
        {\n
            "Sid": "Stmt1444812758000",\n
            "Effect": "Allow",\n
            "Action": [\n
                "ec2:DescribeInstanceStatus",\n
                "ec2:DescribeInstances",\n
                "ec2:StartInstances",\n
                "ec2:StopInstances"\n
            ],\n
            "Resource": [\n
                "*"\n
            ]\n
        },\n
        {\n
            "Action": [\n
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Effect": "Allow",\n
            "Resource": "arn:aws:logs:*:*:*"\n
        }\n
    ]\n
}\n



2)  create a new function in lambda and attach a exising roles, 
    and paste your code here  in  dialog box 
    save 
    
3) switch to ec2 service and mention a tag names that paticular machines 
   for Example : 
   AutoOn:True
   AutoOff: true 
   
Note:   in case if you did not attach any tag name on any machine then  lambda will be did not execute python sccript 
only tag name matched instances only going to be executed 

4) back to your lambda function and Execute -- Test 

5) verify if your machine is sheduled stop/start isntance 

   

    
