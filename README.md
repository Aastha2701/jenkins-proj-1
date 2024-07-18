# Jenkins free style project 😎👇

## 1. Launch AWS EC2 Instance

- Go to AWS Console
- Instances(running) :- ubuntu-22 or other
- t2.micro
- security group :- ssh, http, https, all traffic (anywhere)
- key pair :- jenkins-key.pem
- Launch instances

## 2. Connect EC2 Instance & Install Jenkins

#### Run the below commands to install Java and Jenkins

Install Java

```
sudo apt update
sudo apt install openjdk-11-jre -y
```

Verify Java is Installed

```
java -version
```

Now, you can proceed with installing Jenkins
##### YOU CAN FOLLOW : https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install jenkins -y
jenkins --version
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

**Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

- EC2 > Instances > Click on <Instance-ID>
- In the bottom tabs -> Click on Security
- Security groups
- Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed `All traffic`).

<img width="1187" alt="Screenshot 2023-02-01 at 12 42 01 PM" src="https://user-images.githubusercontent.com/43399466/215975712-2fc569cb-9d76-49b4-9345-d8b62187aa22.png">


### Login to Jenkins using the below URL:

http://(ec2-instance-public-ip-address):8080 

Note: If you are not interested in allowing `All Traffic` to your EC2 instance

      1. Delete the inbound traffic rule for your instance
      
      2. Edit the inbound traffic rule to only allow custom TCP port `8080`
  
After you login to Jenkins, 

      - Run the command to copy the Jenkins Admin Password - 
      
      sudo cat /var/lib/jenkins/secrets/initialAdminPassword
      
      - Enter the Administrator password

# 4. start nodeapp project

goto jenkins dashboard

click create new item

select pipeline project

mention github project section : your github repo url

pipeline : type or use projects syntax

build now✌️✌️✌️✌️
