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


## 3. Login to Jenkins using the below URL:

http://(ec2-instance-public-ip-address):8080 


**Note: ** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

- EC2 > Instances > Click on (Instance-ID)

- In the bottom tabs -> Click on Security
  
- Security groups
  
- Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed `All traffic`).

<img width="1187" alt="Screenshot 2023-02-01 at 12 42 01 PM" src="https://user-images.githubusercontent.com/43399466/215975712-2fc569cb-9d76-49b4-9345-d8b62187aa22.png">

  
After you login to Jenkins, 

- Run the command to copy the Jenkins Admin Password 

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
            
- Enter the Administrator password

Now Install Suggested Plug-ins


## 4. Start Project

Goto jenkins dashboard

Click create new item 

```
my-first-freestyle-project
```

Select freestyle project ---> ok

Mention github project section

```
https://github.com/itscloudevops/freestyle-jenkins.git
```

Source Code Management = git  , Again mention github repo url

Credentials = generate credentials  , Apply and Save

Now Click on Build Now ✌️✌️✌️✌️


## 5. Launch Your App. 🌏

Go to Console Output and copy 👇

/var/lib/jenkins/workspace/my-first-freestyle-project


```
cd /var/lib/jenkins/workspace/my-first-freestyle-project
```

Now Update your machine

```
sudo su
```

```
apt update
```

Now Install nodejs

```
apt install nodejs -y
```

Now Install NPM

```
apt install npm -y
```

Now Set-up NPM

```
npm install
```

Finallllly Expose Your APPLICATION Globally🚀⛳😊🌏

```
node app.js
```

##### Now Access Your App.

copy your instance public-ip:8000
