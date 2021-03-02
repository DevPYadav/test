# Installing jenkins

* $which wget
* $sudo su # this prevents us from having to issue sudo each time.  
* $yum install -y wget  

## Get the jenkins file from the repo
* $sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkin-ci.org/redhat/jenkins.repo
or
* $sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo 

# Import the jenkins key
* $sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
or
* sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key 

* $yum update 
* $yum install jenkins  java-1.8.0-openjdk-devel git -y 
or
* $yum install jenkins
* $yum install java-1.8.0-openjdk

## Starting Jenkins
* $systemctl enable jenkins
* $systemctl start jenkins
* $systemctl status jenkins

##For logging into Jenkins server 
* http://devpyadav6c.mylabserver.com:8080/
* Jenkins user/passwd - cloud_user/*sana1@345

## Get the sudo password 
* $ cat /var/lib/jenkins/secrets/initialAdminPassword
-----------------------------------------------------------------------------------

For installing jenkins, go to the below url and follow the instructions:

https://www.vultr.com/docs/how-to-install-jenkins-on-centos-7


If you are starting nginx, you need to stop the httpd service using the below commands -
1) See what is running on port 80 using the below commands - 

$netstat -tulpn
$systemctl stop httpd -------To stop Apache;
$systemctl disable httpd --------To stop Apache starting on boot;

Stopping and starting jenkins using command line - 
$service jenkins start/stop/restart
----------------------------------------------------------------------------------
3 Steps to Perform SSH Login Without Password Using ssh-keygen & ssh-copy-id

You can login to a remote Linux server without entering password in 3 simple steps using ssky-keygen and ssh-copy-id as explained in this article.

ssh-keygen creates the public and private keys. ssh-copy-id copies the local-host’s public key to the remote-host’s authorized_keys file. ssh-copy-id also assigns proper permission to the remote-host’s home, ~/.ssh, and ~/.ssh/authorized_keys.

Step 1: Create public and private keys using ssh-key-gen on local-host

jsmith@local-host$ [Note: You are on local-host here]

jsmith@local-host$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/jsmith/.ssh/id_rsa):[Enter key]
Enter passphrase (empty for no passphrase): [Press enter key]
Enter same passphrase again: [Pess enter key]
Your identification has been saved in /home/jsmith/.ssh/id_rsa.
Your public key has been saved in /home/jsmith/.ssh/id_rsa.pub.
The key fingerprint is:
33:b3:fe:af:95:95:18:11:31:d5:de:96:2f:f2:35:f9 jsmith@local-host
Step 2: Copy the public key to remote-host using ssh-copy-id

jsmith@local-host$ ssh-copy-id -i ~/.ssh/id_rsa.pub remote-host
jsmith@remote-host's password:
Now try logging into the machine, with "ssh 'remote-host'", and check in:

.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.
Note: ssh-copy-id appends the keys to the remote-host’s .ssh/authorized_key.

Step 3: Login to remote-host without entering the password

jsmith@local-host$ ssh remote-host
Last login: Sun Nov 16 17:22:33 2008 from 192.168.1.2
[Note: SSH did not ask for password.]

jsmith@remote-host$ [Note: You are on remote-host here]
-------------------------------------------------------------------------------
