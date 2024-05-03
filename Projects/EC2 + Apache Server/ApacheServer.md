# Create EC2 instance and Launch an Appach Web Server Application

We will create an ec2 instance and launch an Appache Web Server.

## Prerequisites

    1.Computer with internet access.
    2.AWS Account(Free Tier recommended).
    3.An active default Virtual Private Cloud (VPC).
    4.A public Subnet.
    5. Also its imperative you have familiarity with Bash Sript basic knowledge.

## Objectives

    1.Create and launch an Ec2 instance via the Aws Management Console.
    2.Configure the Security Groups to allow SSH and HTTP connection to the instance.
    3.SSH into Ec2 instance and by using a script install Appache Web Server with  custom webpage.

## Steps

### Step 1: Create and launch an EC2 instance

    1.Sign in to the AWS Management Console: Go to the AWS Management Console and sign in to your account.

    2.Navigate to EC2 Dashboard: Click on "Services" and select "EC2" under the Compute section and launch an Instance.

    3. Select an Amazon Machine Image (AMI) for your instance. You can choose an Amazon Linux 2AMI  AND an  Instance Type: Select the instance type t3.micro.
   
    4.Configure networking settings: Create a security Group which allows ssh(port22) and HTTPS(port80) connections.

    5.Create Key Pair: Choose an existing key pair or create a new key pair to connect to your instance securely via SSH.

    6.Review and Launch: Review your instance configuration and Click "Launch Instances" to create your EC2 instance.

### Step 2: Deploy an Appache Web Server

    1.
        SSH into Ec2 Instance: `` Here we shall copy Public Ip for Code SSH into the instance. 
        - Enter the command below 
``ssh -i your-key.pem ec2-user@your-instance-ip.``

    2.
        switch to the “superuser” to elevate our privileges 
        Enter sudo su and execute the command.

    3.
        create a bash script known as WebServer.sh and input the command to configure the Apache web Server.

 ``#!/bin/bash``

``yum update -y``

``yum install -y httpd``

``systemctl enable httpd``

``systemctl start httpd``

    4.
       add some sample custom data to webpage
       
        ``<!DOCTYPE html>``
        ``<html>``
        ``<head>``
        ``<title>Page Title</title>``
        ``</head>``
        ``<body>``
        ``<p> Welcome to Apache</p>``
        ``</body>``
        ```</html>``
  