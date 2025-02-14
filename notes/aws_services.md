# IAM: Users and Groups

Identity and Access Management

- **Global service**
- **Root** account created by default, shouldn't be used or shared
- **Users** are people within your organization, and can be grouped
- **Groups** only contain users, not other groups
- Users don't have to belong to a group, and user can belong to multiple groups

## IAM: Permissions

- Users or Groups can be assigned JSON documents called policies
- These policies define the permissions of the users
- In AWS you apply the **least privilege principle**: don't give more permissions than a user needs

## IAM Policy Structure

- Consists of:
  - Version: policy language version, always include "20 12-10-17"
  - Id: an identifier for the policy (optional)
  - Statement: one or more individual statements (required)
- Statements consists of:
  - Sid: an identifier for the statement (optional)
  - Effect: whether the statement allows or denies access (Allow, Deny)
- Principal: account/user/role to which this policy applied to
- Action: list of actions this policy allows or denies
- Resource: list of resources to which the actions applied to
- Condition: conditions for when this policy is in effect (optional)

## IAM Password Policy

- Strong passwords = higher security for your account
- In AWS, you can setup a password policy:
  - Set a minimum password length
  - Require specific character types:
    - including uppercase letters
    - lowercase letters
    - numbers
    - non-alphanumeric characters
- Allow all IAM users to change their own passwords
- Require users to change their password after some time (password expiration)
- Prevent password re-use

## IAM Roles for Services

- Some AWS service will need to perform actions on your behalf
- To do so, we will assign permissions to AWS services with IAM Roles
- Common roles:
  - EC2 Instance Roles
  - Lambda Function Roles
  - Roles for CloudFormation
**These roles are not used by people, but by AWS services**

## IAM Security Tools
**IAM Credentials Report (account-level)**
- a report that lists all your account's users and the status of their various credentials

**IAM Access Advisor (user-level)**
- Access advisor shows the service permissions granted to a user and when those services were last accessed.
- You can use this information to revise your policies.

## IAM Guidelines & Best Practices
- Don't use the root account except for AWS account setup
- One physical user = One AWS user
- Assign users to groups and assign permissions to groups
- Create a strong password policy
- Use and enforce the use of Multi Factor Authentication (MFA)
- Create and use Roles for giving permissions to AWS services
- Use Access Keys for Programmatic Access (CLI / SDK)
- Audit permissions of your account using IAM Credentials Report & IAM Access Advisor
- Never share IAM users & Access Keys

## Shared Responsibility Model for IAM
**AWS**
- Infrastructure (global network security)
- Configuration and vulnerability analysis
- Compliance validation

**You/User**
- Users, Groups, Roles, Policies management and monitoring
- Enable MFA on all accounts
- Rotate all your keys often
- Use IAM tools to apply appropriate permissions
- Analyze access patterns & review permissions


# EC2
- EC2 is one of the most popular of AWS' offering
- EC2 = Elastic Compute Cloud = Infrastructure as a Service
- It mainly consists in the capability of :
- Renting virtual machines (EC2)
- Storing data on virtual drives (EBS)
- Distributing load across machines (ELB)
- Scaling the services using an auto-scaling group (ASG)

## EC2 sizing & configuration options
- Operating System (OS): Linux, Windows or Mac OS
- How much compute power & cores (CPU)
- How much random-access memory (RAM)
- How much storage space:
  - Network-attached (EBS & EFS)
  - hardware (EC2 Instance Store)
- Network card: speed of the card, Public IP address
- Firewall rules: security group
- Bootstrap script (configure at first launch): EC2 User Data

## EC2 User Data
- It is possible to bootstrap our instances using an EC2 User data script.
- bootstrapping means launching commands when a machine starts
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
  - Installing updates
  - Installing software
  - Downloading common files from the internet
  - Anything you can think of
- The EC2 User Data Script runs with the root user

## EC2 Instance Types
Has the following naming convention: **m5.2xlarge**
- m: instance class
- 5: generation (AWS improves them over time)
- 2xlarge: size within the instance class

**Compute Optimized**
- Great for compute-intensive tasks that require high performance processors:
  - Batch processing workloads
  - Media transcoding
  - High performance web servers
  - High performance computing (HPC)
  - Scientific modeling & machine learning
  - Dedicated gaming servers

**Memory Optimized**
- Fast performance for workloads that process large data sets in memory
- Use cases:
  - High performance, relational/non-relational databases
  - Distributed web scale cache stores
  - In-memory databases optimized for Bl (business intelligence)
  - Applications performing real-time processing of big unstructured data

 **Storage Optimized**
- Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage
- Use cases:
  - High frequency online transaction processing (OLTP) systems
  - Relational & NoSQL databases
  - Cache for in-memory databases (for example, Redis)
  - Data warehousing applications
  - Distributed file systems

## EC2 Purchasing Options
**On-Demand Instances - short workload, predictable pricing, pay by second**
- Pay for what you use:
  - Linux or Windows - billing per second, after the first minute
  - All other operating systems - billing per hour
- Has the highest cost but no upfront payment
- No long-term commitment
- Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave
  
**Reserved Instances**
- Up to 72% discount compared to On-demand
- You reserve a specific instance attributes (Instance Type, Region, Tenancy, OS)
- Reservation Period - 1 year (+discount) or 3 years (+ + +discount)
- Payment Options - No Upfront (+), Partial Upfront (++), All Upfront (+++)
- Reserved Instance's Scope - Regional or Zonal (reserve capacity in an AZ)
- Recommended for steady-state usage applications (think database)
- You can buy and sell in the Reserved Instance Marketplace
- Convertible Reserved Instances:
  - Can change the EC2 instance type, instance family, OS, scope and tenancy
  - Up to 66% discount

**Savings Plans (| & 3 years) -commitment to an amount of usage, long workload**

**Spot Instances - short workloads, cheap, can lose instances (less reliable)**
- Can get a discount of up to 90% compared to On-demand
- Instances that you can "lose" at any point of time if your max price is less than the current spot price
- The MOST cost-efficient instances in AWS
- Useful for workloads that are resilient to failure:
  - Batch jobs
  - Data analysis
  - Image processing
  - Any distributed workloads
  - Workloads with a flexible start and end time
- Not suitable for critical jobs or databases


**Dedicated Hosts - book an entire physical server, control instance placement**
- Book an entire physical server for your use.  
- Control over **instance placement** (useful for licensing requirements).  
- Allows you to run your workloads on **dedicated hardware**.  
- Provides **visibility into sockets, cores, and host ID** for compliance or licensing needs.  
- Most expensive purchasing option.  
- **Recommended for:**  
  - Software that requires specific server-bound licenses.  
  - Compliance and regulatory requirements where physical isolation is necessary.

**Dedicated Instances - no other customers will share your hardware**
- Instances run on **dedicated hardware**, physically isolated from other AWS customers.  
- Automatically provisions dedicated infrastructure without manual server management.  
- Charged based on the **instance type** and usage.  
- Does not provide visibility into sockets or cores like Dedicated Hosts.  
- **Recommended for:**  
  - Workloads needing physical isolation.  
  - Applications with strict compliance requirements.  

**Capacity Reservations - reserve capacity in a specific AZ for any duration**
- Reserve capacity in a specific **Availability Zone (AZ)** for any duration.  
- Ensures capacity is available when you need it, even during high-demand periods.  
- Can be combined with Savings Plans or Reserved Instances for cost savings.  
- No long-term commitment; you can cancel anytime.  
- **Recommended for:**  
  - Applications with short-term capacity needs.  
  - Ensuring resource availability during important events like launches or migrations.  
  - Critical applications requiring guaranteed capacity.  


