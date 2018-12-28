# ec2-lab-2

## Setup EC2 key pairs

```
Setup and download key pairs before deploy
```

## Deploy

```
Deploy ec2 instance along with instance security group
```

## Access EC2

```
Navigate to directory where your key pair is in the terminal
run "chmod 400 keypair.pem"

Login with ssh: replace x.x.x.x with public ec2 ip address
run "ssh ec2-user@x.x.x.x -i keypair.pem"

```

## Update

```
Apply updates:
run "sudo yum update"
```

## Install Apache

```
Install apache:
run "sudo yum install httpd -y"
```

## Create index.html and run server

```
Navigate to:
cd /var/www/html

Create a simple index.html file
run "sudo nano index.html"

Start Apache service
run "sudo service httpd start"
```

## Website is up and running

```
Navigate to EC2 public ip address in browser
```
