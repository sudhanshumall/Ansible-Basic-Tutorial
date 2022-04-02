## Ansible Ad-hoc commands

- Ansible ad-hoc commands uses one liner command line tools to automate a non-repetitive tasks, the tasks which needs to be performed only 1 time

- Ansible ad-hoc commands are quick and easy but not reusable

**Syntax** :

```
ansible <host> -m <module> -a "<module options>"
```

**Examples** :

1. Check target node connectivity

```
ansible target-node1 -m ping
```

2. Create an empty file on all the target nodes

```
ansible all -m file -a "dest=/home/vagrant/empty-file-ad-hoc.txt state=touch"
```

_**Note** : In above Ansible ad-hoc command, we have used **all** group which will pick all the target nodes mentioned in the inventory file and create the empty file_

3. Installing packages

```
ansible target-node1 -m apt -a "name=apache2 state=present" --become
```

_**Note** : In above Ansible ad-hoc command, we have used **become** keyword because packaging module requires root provileges for installing any packages. Also this ad-hoc commands connects to the target node using the ansible user which we defined in the inventory file i.e **vagrant** but runs the command as the **root** user because we are using **beome** keyword_

**Exercises** : Check your knowledge

1. Write an Ansible ad-hoc command to copy a file to the target nodes
2. Write an Ansible ad-hoc command to install nginx package
3. Write an Ansible ad-hoc command to change the ownership of the file "empty-file-ad-hoc.txt" (which we created in this lesson) to root
4. Write an Ansible ad-hoc command to delete the empty file "empty-file-ad-hoc.txt"
5. Write an Ansible ad-hoc command to check the uptime of the target nodes to check from how long the target nodes are running
