## Ansible Variables

Ansible support the use of variables which helps executing same playbook again and again on different target nodes and environments.

**Valid variable names**: Variable names should be letters, numbers, and underscores and should always start with a letter.

Different ways of using variables:

**1. Variables in Playbooks**

Syntax:

```
vars:
  variable_name: value
```

**Playbook Exmaple 1** :

![image](https://drive.google.com/uc?export=view&id=1OW2hHqX3VAxZP9Vj91c3vgTLZWlw2J_a)

**Playbook Exmaple 1 Explanation** : Here in **example-1-variable-in-playbook.yaml** ansile playbook, we have only 1 task and the variable used is "message" and value assigned to it is **"Hello Sudhanshu"**.

**Task 1** : Name of task 1 is **"ansible variable basic use case"**. It is using **debug** module (part of utilities module) which prints the statements during execution can be useful for debugging variables or expressions without necessarily halting the playbook.

**To Run the Playbook** :

```
ansible-playbook -i my-inventory example-1-variable-in-playbook.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=18RXCewO1GuwM9D1OPQjQ8HXlnuJ4B-LW)

**2. Variables with Arrays**

Syntax:

```
vars:
  variable_name:
    - value1
    - value2
    - value3

```

**Playbook Exmaple 2** :

![image](https://drive.google.com/uc?export=view&id=1ys2A6FsMxhcJ3356SHcKu9U02RDaJTCS)

**Playbook Exmaple 1 Explanation** : Here in **"example-2-variable-with-arrays.yaml"** ansible playbook, we have only 1 task and the variable "fruits" contains list of 4 fruits and we can use index to get any particular fruit.

**Task 1** : Name of task 1 is **"ansible list variable example"**. It is also using **debug** module and printing the first index (second element from list) value in the terminal.

**To Run the Playbook** :

```
ansible-playbook -i my-inventory example-2-variable-with-arrays.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1K-fsydvmQKH-CCeRgpZqxWSa9cmGPU_Y)

**3. Variables with Dictionary**

Syntax:

```
vars:
  list_variable_name:
    dictionary_variable_name1:
        key1: value1
        key2: value2
    dictionary_variable_name2:
        key1: value1
        key2: value2
```

**Playbook Exmaple 3** :

![image](https://drive.google.com/uc?export=view&id=13Ma-oLsfOIWanCIyXK19MWH93AYk4Sck)

**Playbook Exmaple 3 Explanation** : Here in **"example-3-variable-with-dictionary.yaml"** ansible playbook, we have only 1 task and the variable students contains list of dictionaries.

**Task 1** : Name of task 1 is **"ansible dictionary variable example"**. It is using debug module and printing the age of Sudhanshu.

**To Run the Playbook** :

```
ansible-playbook -i my-inventory example-3-variable-with-dictionary.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1ciAA5wObB3KsC53UQXz8ApJkPQm_fbat)

**4. Variables in inventory file**

```
target-node1 ansible_host=192.168.56.11 ansible_user=vagrant
target-node2 ansible_host=192.168.56.12 ansible_user=vagrant
```

We have already used this when we defined our inventory file for the ver first time.
So, "**ansible_host**" and "**ansible_user**" are the variable we used in our inventory file without even knowing that we already have been using variables when runing our ansible playbooks.

![image](https://drive.google.com/uc?export=view&id=1yhfRk4kefvnylcu9R8de4XEGXymHA7-V)

**Playbook Exmaple 4 Explanation** : Here in **"example-4-variable-in-inventory-file.yaml"** ansible playbook, we have only 1 task and we are using the variable defined in the inventory file.

**Task 1** : Name of task 1 is **"variable in inventory file example"** and it is also using debug module and printing the statement using **ansible_host** variable which will evaluate the variable and print the IP of the target node where the playbook is running.

**To Run the Playbook** :

```
ansible-playbook -i my-inventory example-4-variable-in-inventory-file.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1akRGTzRlgtniSOZ4ExBvu_6Smz8s0Q99)

**5. Host Variables**

In a host variable file, variable applies to only 1 host for which it has been created.
The host variable is usually stored under /etc/ansible/host_vars directory

**Note** : For simplicity, we will be using our default inventory file under **/etc/ansible/hosts** for this example

**Steps to create host variables** :

- Create a new directory "host_vars" under /etc/ansible/

```
mkdir /etc/ansible/host_vars
```

- Create new file for the respective target node under /etc/ansible/host_vars/, in this case for target-node1

```
touch /etc/ansible/host_vars/target-node1
```

- Add the variable details "ansible_host: 192.168.56.11" and "ansible_user: vagrant" for target-node1 inside **/etc/ansible/host_vars/target-node1** file

```
ansible_host: 192.168.56.11
ansible_user: vagrant
```

- Remove "ansible_host=192.168.56.11" and "ansible_user=vagrant" variable from inventory file (/etc/ansible/hosts) for target-node1 and update inventory file as below

```
target-node1
target-node2 ansible_host=192.168.56.12 ansible_user=vagrant
```

![image](https://drive.google.com/uc?export=view&id=1-lk4vilYeOSlsAHtxK16FRkDfxltry7t)

**Playbook Exmaple 5 Explanation** : Here in **"example-5-host-variable.yaml"** ansible playbook, we have only 1 task and we are accessing the variable defined in the host vars directory for target-node1.

**Task 1** : Name of task 1 is **"variable in host var file"**. It is using debug module to print the variables defined in host vars directory.

**To Run the Playbook** :

```
ansible-playbook example-5-host-variable.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1YrXsLkTSGbzLnTs2cz8S1h6GKTIRor6N)

**6. Group Variables**

Group variables are a convenient way to apply variables to multiple hosts at once. If the target nodes share the same values, then we can create a group variable file under /etc/ansible directory. In our case, we have "ansible_user" variable which shares the same value for both the target nodes.

**Note** : For simplicity, we will be using our default inventory file under **/etc/ansible/hosts** for this example

Let's add our both target nodes in a group and update our inventory (/etc/ansible/hosts) as below:

```
[mygroup]
target-node1
target-node2 ansible_host=192.168.56.12 ansible_user=vagrant
```

Here, **[mygroup]** is the group name and now both the target nodes belongs to this group.

Let's see how we can create group variable file

**Steps to create group variables** :

- Create a new directory "group_vars" under /etc/ansible/

```
mkdir /etc/ansible/group_vars
```

- Create new file for the respective group under /etc/ansible/group_vars/, in this case for group "mygroup" (here the name of the file should be same as the group name created in inventory file)

```
touch /etc/ansible/host_vars/mygroup
```

- Add the common variable "ansible_user: vagrant" which is used for both the target nodes, as below

```
ansible_user: vagrant
```

- Remove "ansible_user: vagrant" variable from inventory file (/etc/ansible/hosts) and update inventory file as below

```
[mygroup]
target-node1
target-node2 ansible_host=192.168.56.12
```

- Also, remove the "ansible_user: vagrant" variable from the host variable file we created in previous example and update **/etc/ansible/host_vars/target-node1** file as below (ansible_user variable will be evaluated from the group variable now)

```
ansible_host: 192.168.56.11
```

![image](https://drive.google.com/uc?export=view&id=1-JkAPBfz2k4LpH79dfq7loCLz_pxZqKD)

**Playbook Exmaple 6 Explanation** : Here in **"example-6-group-variable.yaml"** ansible playbook, we have only 1 task and we are using accessing variable defined in group vars. Also, note **hosts** section where we have used the group name which was defined in the inventory file (/etc/ansible/hosts).

**Task 1** : Name of task 1 is **"variable in group var file"**. It is using debug module to print the variables defined in group vars directory. Also this task will be triggered on both the target nodes as we have used groups and both target nodes belogs to the group.

**To Run the Playbook** :

```
ansible-playbook example-6-group-variable.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=16Nxd8JUM9iHiKSqB88Ugsw1piC0xZMmh)

**7. Importing variable from another files**

We can also define a variable in a separate yaml file and import it in our playbook using **vars_files** YAML tag.

![image](https://drive.google.com/uc?export=view&id=1HViSqQUvSycjlcmWfPFTOXnTwEX29lDU)

**Playbook Exmaple 7 Explanation** : Here in **"example-7-variables-imported-file.yaml"** ansible playbook, we have only 1 task and we are using another file to import the variable using **vars_files** YAML tag.

**Task 1** : Name of task 1 is **"import var from file"**. It is using debug module and printing the variable (myname) defined in another file i.e **example-7-variable-file.yaml** (file is added in this lesson).

**To Run the Playbook** :

```
ansible-playbook example-7-variables-imported-file.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1sh7EGfuNG0rBrXgagZFF-jzacmKDc_kq)

**8. Command line variables**

variables can also be passed on command line using "--extra-vars" or "-e" argument in "key=value" format

![image](https://drive.google.com/uc?export=view&id=1wg5SCZnxsSjuoEuSYLDQuyHk3eVuaJTe)

**Playbook Exmaple 8 Explanation** : Here in **"example-8-command-line-variable.yaml"** ansible playbook, we have only 1 task and we will be passing the command line variable while running the playbook.

**Task 1** : Name of task 1 is **"command line variable"**. It is using debug module to print the variable which will be passed through command line while running the playbook.

**To Run the Playbook** :

```
ansible-playbook example-8-command-line-variable.yaml --extra-vars "myname=sudhanshu"
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1BGsMx7g0FN0yXp_8lD5Sd4NJr1lerlMJ)

**Important Note** : Command line variables are given the highest precedence and it can override if the same variable is defined in other places like host vars, grooup vars, another file etc.

Now, if we run our previous ansible playbook **"example-7-variables-imported-file.yaml"** where we imported variable from different YAML file by passing **extra-vars**, then it will override the variable value.

**To Run the Playbook** :

```
ansible-playbook example-7-variables-imported-file.yaml --extra-vars "myname=sudhanshumall"
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1OfhccSdMn1VVD2aOUKVO3GvDci07m_A7)

**Note** : Now in the output, you can see that the variable which is defined in **example-7-variable-file.yaml** is getting overidden when used **extra-vars** while running the playbook and variable value is coming as **sudhanshumall** instead of **sudhanshu** (which is defined in **example-7-variable-file.yaml**)

**9. Ansible Register**

Ansible register is a way of storing the output of the command or a task into a variable

Synatx :

```
register: command_output
```

![image](https://drive.google.com/uc?export=view&id=1sYGiIb0ld1tvr_Oo-jOvUSG5h2EwFnyu)

**Playbook Exmaple 8 Explanation** : Here in **"example-9-register-variable.yaml"** ansible playbook, we have 2 tasks running on target node 1.

**Task 1** : Name of task 1 is **"get hostname of the target machine"**. It is using command module to run **hostname** command on target-node1 machine and storing its output using **register** variable.

**Task 2** : Name of task 2 is **"printing hostname value"**. It is using debug module to print the value of the variable stored using register.

**Output** :

![image](https://drive.google.com/uc?export=view&id=1p_K4KsCm8XEB9yR1RVAZV29gYCrLBICX)
