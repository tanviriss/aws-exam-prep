# Cloud Computing

- Cloud computing is the **on-demand** delivery of compute power, database storage, applications, and other IT resources
- You can provision exactly the right type and size of computing resources you need
- Simple way to access servers, storage, databases and a set of application services

Amazon Web Services owns and maintains the network-connected hardware required for these application services, while you provision and use what you need via a web application.

## The Deployment Models of the Cloud

Private Cloud:

- Cloud services used by a single organization, not exposed to the public.
- Complete control
- Security for sensitive applications
- Meet specific business needs

Public Cloud:

- Cloud resources owned and operated by a third-party cloud service provider delivered over the Internet.
- Six advandtages of cloud computing

Hybrid Cloud:

- Keep some servers on premises and extend some capabilities to the Cloud
- Control over sensitive assets in your private infrastructure
- Flexibility and cost-effectiveness of the public cloud

## The Five Characteristics of Cloud Computing

- On-demand self service:
  - Users can provision resources and use them without human interaction from the service provider
- Broad network access:
  - Resources available over the network, and can be accessed by diverse client platforms
- Multi-tenancy and resource pooling:
  - Multiple customers can share the same infrastructure and applications with security and privacy
  - Multiple customers are serviced from the same physical resources
- Rapid elasticity and scalability:
  - Automatically and quickly acquire and dispose resources when needed
  - Quickly and easily scale based on demand
- Measured service:
  - Usage is measured, users pay correctly for what they have used

## Six Advantages of Cloud Computing

- Trade capital expense (CAPEX) for operational expense (OPEX)
  - Pay On-Demand: don't own hardware
  - Reduced Total Cost of Ownership (TCO) & Operational Expense (OPEX)
- Benefit from massive economies of scale
  - Prices are reduced as AWS is more efficient due to large scale
- Stop guessing capacity
  - Scale based on actual measured usage
- Increase speed and agility
- Stop spending money running and maintaining data centers
- Go global in minutes: leverage the AWS global infrastructure

## Problems solved by the Cloud

- Flexibility: change resource types when needed
- Cost-Effectiveness: pay as you go, for what you use
- Scalability: accommodate larger loads by making hardware stronger or adding additional nodes
- Elasticity: ability to scale out and scale-in when needed
- High-availability and fault-tolerance: build across data centers
- Agility: rapidly develop, test and launch software applications

## 3 Pricing of AWS Cloud

- Computer
- Storage
- Data Transfer out of AWS Cloud

## Example of Cloud Computing Types

- Infrastructure as a Service:
  - Amazon EC2 (on AWS)
  - GCP, Azure, Rackspace, Digital Ocean, Linode
- Platform as a Service:
  - Elastic Beanstalk (on AWS)
  - Heroku, Google App Engine (GCP), Windows Azure (Microsoft)
- Software as a Service:
  - Many AWS services (ex: Rekognition for Machine Learning)
  - Google Apps (Gmail), Dropbox, Zoom

## Aws Regions

- AWS has Regions all around the world
- Names can be us-east-I, eu-west-3...
- A region is a cluster of data centers
- Most AWS services are region-scoped
- Each region has many availability zones (usually 3, min is 3, max is 6).
- Each availability zone (AZ) is one or more discrete data centers with redundant power, networking, and connectivity

## AWS Points of Presence (Edge Locations)

- Amazon has 400+ Points of Presence (400+ Edge Locations & 10+
- Regional Caches) in 90+ cities across 40+ countries
- Content is delivered to end users with lower latency

## Shared Responsibility

- **CUSTOMER** = RESPONSIBILITY FOR THE SECURITY <u>IN</u> THE CLOUD
- **AWS** = RESPONSIBILITY FOR THE SECURITY <u>OF</u> THE CLOUD

## Security Groups 

- They control how traffic is allowed into or out of our EC2 Instances.
- Security groups only contain allow rules
- Security groups rules can reference by IP or by security group
- Security groups are acting as a "firewall"' on EC2 instances
- They regulate:
  - Access to Ports
  - Authorised IP ranges - IPv4 and IPv6
  - Control of inbound network (from other to the instance)
  - Control of outbound network (from the instance to other)
- Can be attached to multiple instances
- Locked down to a region /VPC combination
- Does live "outside" the EC2 - if traffic is blocked the EC2 instance won't see it
- It's good to maintain one separate security group for SSH access
- If your application is not accessible (time out), then it's a security group issue
- If your application gives a "connection refused" error, then it's an application error or it's not launched
- All inbound traffic is blocked by default
- All outbound traffic is authorised by default

## Classic Ports

- 22 = SSH (Secure Shell) - log into a Linux instance
- 21 = FTP (File Transfer Protocol) - upload files into a file share
- 22 = SFTP (Secure File Transfer Protocol) - upload files using SSH
- 80 = HTTP - access unsecured websites
- 443 = HTTPS - access secured websites
- 3389 = RDP (Remote Desktop Protocol) - log into a Windows instance

  
## SSH Summary Table
- SSH is one of the most important function. It allows you to control a remote machine, all using the command line.
<img width="600" alt="image" src="https://github.com/user-attachments/assets/e57be4c3-3cd9-49a9-9b12-098fdba69ede" />

- Command for mac/linux:
  - ssh -i EC2Tutorial.pem(this is the pem file from the instance) ec2-user@3.250.26.200(this is the public ipv4 server)


