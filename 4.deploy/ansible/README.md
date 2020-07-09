## Understanding core components of Ansible:

### Overview:
- Inventories
- Modules: tools that ansible uses to execute commands on remote system.
- Variable: Customizing various configurations as you work with ansible.
- Facts: Special Type of variable that allows us 
- plays,playbooks : To orchestrate various modules into overall tasks that help us in achievw goal.
- Configuration files: These are the way we configure ansible to behave as we desired.

### Inventories:
- Inventories are how ansible can locate and run aganist multiple-systems.
- you cam think of an inventory as a list of hosts.
- By default, Ansible uses /etc/ansible/hosts as its inventory but this is configurable.
- Inventories may be formated as "INI file" or as a yaml file. Note: File formats are interchangeable.
Example:
  all:
   hosts:
    abcmail.example.com
   children:
    webservers:
     hosts:
      webi.example.com
      web2.example.com
    dbservers:
     hosts:
      db1.example.com
      
- Inventory file may simply consist of a list of hostnames but can be much more robust.
- It is possible to define graphs of hosts,host or group level variables , and groups of groups within the inventory.
- There are a number of variables that may be used within the inventory to control how ansible connects to and interacts with target hosts.


## Installation:
you can use default ec2-keypair (generated and attached to ec2) in using ansible. In this case you don't need to add anything in the authorized file of host-server.

But generally a specific user is created when using ansible . And its public key is copied in authorized-file of host-server.And via private key we will login.




Steps:
FOr Amazon Ec2
- yum install python
- yum install python-pip
- pip install ansible
- [root@ansible-control-node ~]# ansible --version
ansible 2.9.10
  config file = None
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python2.7/site-packages/ansible
  executable location = /usr/local/bin/ansible
  python version = 2.7.18 (default, May  7 2020, 09:20:17) [GCC 4.8.5 20150623 (Red Hat 4.8.5-28)]


- sudo adduser ansibleuser (FOR UBUNTU: sudo adduser newuser --disabled-password )
- su - ansibleuser
- [ansibleuser@ansible-control-node ~]$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ansibleuser/.ssh/id_rsa):
Created directory '/home/ansibleuser/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/ansibleuser/.ssh/id_rsa.
Your public key has been saved in /home/ansibleuser/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:ezL9YDh1GQDxxf1rQ+SExosXhFeqjpXemduvwOZjlFk ansibleuser@ansible-control-node
The key's randomart image is:
+---[RSA 2048]----+
|        oo..=oo. |
|         . +.*oo |
|          . =.*. |
|           .o=Eo.|
|        S .+++. .|
|         ==o= o+ |
|        *.=+++. .|
|         * =o.o  |
|           .oo.oo|
+----[SHA256]-----+
[ansibleuser@ansible-control-node ~]$


- you can create a new-user in host server or youcan use ec2-user/ubuntu(this user is better i guess if more number of servers are there)
- Generally , a user (with some common name) is created in all host-servers and  authroized-file of host-servers is been edited/added with pub;ic-key of ansible-control-node

On host-server:
- sudo useradd ansiblehostuser

-sudo su -
- [ansiblehost1user@host-node ~]$ mkdir .ssh
[ansiblehost1user@host-node ~]$ chmod 700 .ssh
[ansiblehost1user@host-node ~]$ touch .ssh/authorized_keys
[ansiblehost1user@host-node ~]$ chmod 600 .ssh/authorized_keys
[ansiblehost1user@host-node ~]$ vim .ssh/authorized_keys


Added the public key of control-node-ansible user here and in sg-rules also allowed control-node-server ip

[ansibleuser@ansible-control-node ~]$ ssh ansiblehost1user@172.31.47.246

This automatically logged in to host-server. since id_rsa is present in ~/.ssh folder of control-node it is not asking password. but it is good practice if you delete id_rsa(private key) from server and keep it safely


-go to : sudo vim /etc/sudoers
you can use ' echo "ansadmin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers ' : for adding ansiblehostuser in host-server sudo users.
or add entry in the file as "ansiblehost1user         ALL=(ALL)       NOPASSWD: ALL"


## Ansible-playbooks:




reference:
https://github.com/ValaxyTech/DevOpsDemos/blob/master/Ansible/Ansible_installation.MD
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/managing-users.html      



