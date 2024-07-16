# docker-jenkins-declarative-nodeapp😎👇

# 1. install jenkins on ubuntu

apt update

apt install fontconfig openjdk-11-jre -y

<go to jenkins.io => copy binary file & key file>

apt update

apt install jenkins -y

systemctl enable --now jenkins


# 2. for connect jenkins

copy server public-ip:8080

cat /var/lib/jenkins/secrets/initialadminpassword

install suggested plug-ins

# 3. docker permission

apt install docker.io -y

usermod -aG docker jenkins

systemctl restart jenkins

# 4. start nodeapp project

goto jenkins dashboard

click create new item

select pipeline project

mention github project section : your github repo url

pipeline : type or use projects syntax

build now✌️✌️✌️✌️
