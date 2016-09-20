MTN.*NIX.11 Automated Environment Configuration Management
---

***Student***: [Uladzislau Charches](https://upsa.epam.com/workload/employeeView.do?employeeId=4060741400038705754#emplTab=general)

# Puppet lesson_11

**Task1 was easy**

**Task2**

**1. I edited 2 Vagrantfiles. Run it with edited files "host" on client VM. You can check it below**

[Vagrantfile-client]()
[Vagrantfile-server]()

**Server-side (All operations we should do on root)** 
$ sudo rpm -Uvh https://yum.puppetlabs.com/puppetlabs-release-pc1-el-6.noarch.rpm
$ sudo yum install -y puppetserver
$ puppet resource service puppetserver ensure=running (service puppetserver start)
$ puppet resource service puppet ensure=running (service puppet start) 

**Client-side (All operations we should do on root)**
## We need to check the name of our server in etc/hosts --- if ok --->
$ rpm -Uvh https://yum.puppetlabs.com/puppetlabs-release-pc1-el-6.noarch.rpm
$ yum install -y puppet-agent
service puppet start (reconnect to root session because it need to rewrite bash_profile)

##(this command generates sign-cert request to server if we didn't use puppet-agent -t --server server.minsk.epam.com --waitforcert 90 --test) 

**2 Signing of cert and installing ntp module**
**Server-side:**

**To sign Cert**
$ puppet cert list
$ puppet cert sign client.minsk.epam.com

**Installation ntp module**

$ puppet module install puppetlabs-ntp

Creating manifest:
$ vi /etc/puppetlabs/code/environments/production/manifests/day1.pp

[manifest]()

Screenshots:

**Certificates**

![1](https://github.com/VladCharches/Chef-courses/blob/exit_task/screens/1.png)

**Client-side:**

$ puppet agent --server server.minsk.epam.com -t

[log.manifest.log]()

