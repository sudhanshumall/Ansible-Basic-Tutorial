## Ansible Inventory

- Ansible works against multiple managed hosts/nodes in your infrastructure at the same time by using list or group of lists which is known as inventory.

- Default location - /etc/ansible/hosts

- You can define different custom inventory file at the command line by using –i option

- All the hosts in the Ansible inventory file belongs to **all** group(by default)

**Example**

```
ansible-playbook –i <custom-inventory-file-path> ansible-playbook-file
```

_**Note** : If you do not specify custom inventory file using "-i" option, then Ansible will look for the hosts in the /etc/ansible/hosts inventory file_

- The format in the inventory file (/etc/ansible/hosts) is in the INI format

_Note : An INI file is a text-based configuration file with a structure and syntax like key-value pairs for defining the properties_
