## Ansible Inventory Format

<IP1> ansible_user=<username> ansible_ssh_pass=<pwd>
alias-name ansible_host=<IP2> ansible_user=<username> ansible_ssh_pass=<pwd>
<IP3>

Note : This is how we define hosts in the inventory file. You can see above that we have passed **ansible_ssh_pass** where we are stroing the target node password, which is required when you are not using password less ssh connection. However in this tutorial we have setup password less ssh connection and hence wont be using **ansible_ssh_pass** in our inventory file

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
