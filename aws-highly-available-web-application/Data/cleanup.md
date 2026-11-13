Cleanup steps

Delete in this order:
1.	Auto Scaling Group (this terminates the instances)
2.	Load balancer, then target group
3.	Launch template.
4.	VPC: first detach and delete the Internet Gateway, then delete the subnets and the custom route table, then the VPC itself
5.	Security groups, IAM role, SNS topic, CloudWatch alarms and dashboard
6.	ACM certificate and Route 53 records (a hosted zone costs about $0.50/month if kept)
