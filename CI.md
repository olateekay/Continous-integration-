# Simulating a typical CI/CD Pipeline for a PHP Based application

In this project,we will be tasked with creating a pipeline that simulates continuous integration and delivery. We will have a `TODO` Web Applications are based on an interpreted (scripting) language (PHP). It means, it can be deployed directly onto a server and will work without compiling the code to a machine language.

The problem with that approach is, it would be difficult to package and version the software for different releases. And so, in this project, rather than downloading directly from git, we will be using Ansible `uri` module.

Target end to end CI/CD pipeline is represented by the diagram below.

![alt text](https://github.com/olateekay/Continous-integration-/blob/main/Images/image1.png)

## Set Up
This project will require a lot of servers to simulate all the different environments from `dev/ci` all the way to `production`. 

To start with, we will focus on these environments initially.

- Jenkins server - Redhat
- Sonarqube server - Ubuntu
- Artifactory server - Redhat
- Todo server
- DB server 

### Step 1 - Install Dependencies

Spin up a RedHat server and name it “Jenkins”

```
# install remi repo, php and git

yum install -y dnf-utils http://rpms.remirepo.net/enterprise/remi-release-8.rpm
yum install -y  git
yum module reset php -y
yum module enable php:remi-7.4 -y
yum install -y php  php-common php-mbstring php-opcache php-intl php-xml php-gd php-curl php-mysqlnd php-fpm php-json
systemctl start php-fpm
systemctl enable php-fpm


# install java

# open the bash profile 
sudo vi .bash_profile 

# paste the below in the bash profile
export JAVA_HOME=$(dirname $(dirname $(readlink $(readlink $(which javac)))))
export PATH=$PATH:$JAVA_HOME/bin
export CLASSPATH=.:$JAVA_HOME/jre/lib:$JAVA_HOME/lib:$JAVA_HOME/lib/tools.jar

# reload the bash profile
source ~/.bash_profile


# install ansible and jenkins
sudo yum install ansible

Sudo yum install wget
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum upgrade
sudo yum install jenkins
sudo systemctl daemon-reload
sudo systemctl status jenkins

# installing composer
curl -sS https://getcomposer.org/installer | php 
sudo mv composer.phar /usr/bin/composer

# Verify Composer is installed or not
composer --version


# install phpunit, phploc
dnf --enablerepo=remi install php-phpunit-phploc
get -O phpunit https://phar.phpunit.de/phpunit-7.phar
chmod +x phpunit
```
