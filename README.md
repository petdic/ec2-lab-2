# ec2-lab-2

```
Contains 2 EC2 Instances along with EBS's (Elastic Block Store) and an EFS (Elastic File Server)

Contains ElasticLoadBalancer
Ensure ElasticLoadBalancer SecurityGroup is same as Ec2Instance

Ensure that MountTargets are in same AvailabilityZones as EC2Instances.
You can add more MountTargets to ensure all AvailabilityZones are covered.
For MountTargets change SubnetId and SecurityGroups.
Ensure that the EC2 Instance SecurityGroups contains same security group as MountTarget SecurityGroups (default - security group (VPC))
```

## Setup EC2 key pairs

```
Setup and download key pairs before deploy
```

## Deploy

```
Deploy CloudFormation
run "sls deploy"
```

## Access all EC2 Instances

```
Navigate to directory where your key pair is in the terminal
run "chmod 400 keypair.pem"

Login with ssh: replace x.x.x.x with public ec2 ip address
run "ssh ec2-user@x.x.x.x -i keypair.pem"

Navigate to Root directory
run "cd /"

Gain Root privilege
run "sudo su" - sudo not needed for commands

```

## Bash Script

```
EC2 Instances have bash scripts attached to skip the Server Step below.
This is accomplished by creating a bash script.
The script is then converted into base64 by using the command "base64 ec2_startup.sh > ec2_startup.sh.base64"
The ec2_startup.sh.base64 is then attached to UserData for the EC2Instances, this will run automatically when the instances are created.
```

## Server Step - Update Server, Install Apache and Run Apache on all EC2 Instances

```
Apply updates:
run "sudo yum update"

Install apache:
run "sudo yum install httpd -y"

Start Apache service
run "sudo service httpd start"
```

## Mount EFS

```
Navigate to EFS in AWS Console
Locate EFS and select Amazon EC2 mount instructions
Mount the file system using the NFS client - if you using Amazon Linux AMI else follow all instructions
*Note* at end of command, the directory to be mounted must be /var/www/html not /efs for Apache
```

## Create index.html, this should be shared on all EC2 Instances

```
Navigate to:
cd /var/www/html

Create a simple index.html file
run "sudo nano index.html"
```

## Website is up and running

```
Navigate to EC2 Load Balancer in AWS Console and copy DNS Name into web browser
```
