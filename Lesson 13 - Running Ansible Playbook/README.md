## Running Ansible Playbook

We have already seen how to run an Ansible playbook in **Lesson 11 - Writing Ansible Playbook**, but let's see the other ways also.

**Syntax** :

```
ansible-playbook -i <custom-inventory-file-path> <ansible playbok>
```

**Examples** :

1. When using default inventory file (/etc/ansible/hosts)

```
ansible-playbook <playbook-name>.yaml
```

2. When using custom defined inventory file

```
ansible-playbook -i <custom-inventory-file> <playbook-name>.yaml
```

3. When passing run time variables using **--extra-vars** or **-e**

```
ansible-playbook  <playbook-name>.yaml --extra-vars "ansible_user=vagrant"
```

OR

```
ansible-playbook  <playbook-name>.yaml -e "ansible_user=vagrant"
```

For defining more than 1 variables, use spaces between the variables, as mentioned below:

```
ansible-playbook  <playbook-name>.yaml -e "ansible_user=vagrant ansible_host=192.168.56.11"
```
