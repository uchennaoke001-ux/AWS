# Highly Available, Self-Healing HTTPS Web App
# Project Overview
This project demonstrates the design and implementation of a highly available, scalable, self-healing web application architecture on AWS. A small web page shows which server and Availability Zone (AZ) served each request. It is deployed across two Availability Zones behind an Application Load Balancer (ALB) with HTTPS, running on an Auto Scaling Group (ASG) of EC2 instances.
The application itself is deliberately simple so that the infrastructure is the focus. The project is proven by deliberately breaking the system (terminating servers, stopping the app, removing an AZ, generating load) and observing that it recovers on its own
# Objectives
The primary objectives of this project are:

1.	High availability: deploy instances across multiple Availability Zones so the loss of one AZ does not take the application offline.
2.	Automatic traffic distribution: use an Application Load Balancer to spread incoming requests across healthy instances.
3.	Self-healing: use ELB health checks with the Auto Scaling Group so failed or unhealthy instances are terminated and replaced automatically.
4.	Scalability: use a target tracking scaling policy so capacity grows and shrinks with demand.
5.	Secure access: serve traffic over HTTPS using an ACM certificate, restrict instance access to the load balancer only, and use Session Manager instead of SSH.
6.	Observability: monitor the system with CloudWatch alarms, a dashboard and SNS email notifications.
# Architecture
