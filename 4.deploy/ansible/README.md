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


      
