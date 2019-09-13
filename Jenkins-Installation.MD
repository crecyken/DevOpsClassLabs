# Jenkins Installation on Centos 

``` sh 
# Install java-1.8.0-openjdk-devel

sudo yum install -y java-1.8.0-openjdk-devel


# Install the repo and key, and then install Jenkins

 sh sudo yum install -y wget

# Download the repo.

sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo

# Import the required key.

sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key

# Install Jenkins.
sudo yum install -y jenkins
```
