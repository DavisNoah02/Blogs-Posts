# Important EC2 cmds

``CURL & WGET``

A. CURL
      -Command Line utility for transfering data with URLs.
       Can download and upload files.
  
      EXAMPLE ;
       ``curl https://example.com/file.txt -o output.txt``

B. WGET
     - Command Line utility for ONLY downloading files with URLs.
  
          EXAMPLE 
          ``wget https://example.com/file.txt``

  ``+ Both support HTTP,HTTPS,FTP AND FTPS Protocals.``

## Curl commands

    1.Retrieve InstanceId.
     ``` curl http://169.254.169.254/latest/meta-data/instance-id ```
    
    2.Retrieve InstanceType.
     ``` curl http://169.254.169.254/latest/meta-data/instance-type ```
    
    3.Retrieve IAM Role name.
     ``` curl http://169.254.169.254/latest/meta-data/iam/security-credentials/ ```
    
    4.Retrieve Public IP Address.
     ``` curl http://169.254.169.254/latest/meta-data/public-ipv4 ```
  
    5.Retrieve AZ.
     ``` curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone ```

## Getting Instance status

     ``` aws ec2 describe-instance-status --instance-ids {instanceid} --query 'InstanceStatuses[*].[InstanceId,InstanceState.Name]' --output text ```

     ```aws ec2 describe-instances --instance-ids $INSTANCE --query 'Reservations[].Instances[].State.Name' --output text```

## Getting InstanceId with its Name

     ``` aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId,State.Name,Tags[?Key==`Name`].Value]' ```

## Stopping an instance

    ```aws ec2 stop-instances --instance-ids <instance-id>```
