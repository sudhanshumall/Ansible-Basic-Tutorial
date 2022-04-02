## Ansible Inventory Format

```
<IP1> ansible_user=<username> ansible_ssh_pass=<pwd>
alias-name ansible_host=<IP2> ansible_user=<username> ansible_ssh_pass=<pwd>
<IP3>
```

**Note** : This is how we define hosts in the inventory file. You can see above that we have passed **ansible_ssh_pass** where we are stroing the target node password, which is required when you are not using password less ssh connection. However in this tutorial we have setup password less ssh connection and hence wont be using **ansible_ssh_pass** in our inventory file

**Examples :**

```
abc.example.com
192.168.1.40
```

OR

```
[dbservers]  
db1.example.com  
```

OR

```
abc.example.com
192.168.1.40
[appservers]
app1.example.com
app2 ansible_host=app2.example.com ansible_user=ubuntu
```

Now let's recall our **Lesson 5 - Lab Setup**, where we created 2 target nodes. Using those those target nodes, we will create our Ansible inventory file

Update your default inventory file (/etc/ansible/hosts) as below:

```
target-node1 ansible_host=192.168.56.11 ansible_user=vagrant
target-node2 ansible_host=192.168.56.12 ansible_user=vagrant
```

_**Note**: Make sure to use the correct IP of the VM you created (in case the IP you used is different than above)_
