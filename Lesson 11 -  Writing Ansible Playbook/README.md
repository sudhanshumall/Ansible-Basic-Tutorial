## Writing Ansible Playbook

- **Paybook** : is a single YAML file and could contain single or multiple plays in it.

A playbook is a set of multiple **YAML tags**, as mentioned below:

- **name** : It specifies the name of the Ansible playbook.

- **hosts** : Here we define the single host or list of hosts or group of hosts and this tag is mandatory.

- **vars** : This tag lets you to define the variable which you can use in the playbook.

- **tasks** : This is the main section and contains tasks or list of tasks to be executed on the target node. A task futher contains the name of the task and each task is linked to the module which gets executed on the target node.

_Note : **#** is used for comment in the Ansible playbook_

**Example :**

_Below is the structure of an Ansible playbook_

![image](https://drive.google.com/uc?export=view&id=1QsWURxTdBy_ioIvIc__W-trBz3p3Reb9)

**Playbook explanation** : In this playbook, we have only 1 task and it is using an Ansible module called **ping**, which we are using to check the connectivity between Ansible Controller machine and target node

**To Run the Playbook** : ansible-playbook example-1-sample-playbook.yaml

**Output** :

![image](https://drive.google.com/uc?export=view&id=1j7CVntlXo69LGbIjGJAMIrTlGdGgSB_3)

_**Note : Ignore warnings**_
