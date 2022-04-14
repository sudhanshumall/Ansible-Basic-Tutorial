## Ansible Conditionals

In ansible, while writing playbooks there could be times when you want to excute a task based on some condition. When a condition is met, the tasks should be executed else skip it.
Ansible conditionals becomes really important when you are working on many target node with different operating systems and want to write a single playbook based on the different operating systems.

Below are few list of main conditional mostly used:

1. when-conditionals
2. loop and conditionals
3. register variables with conditionals

Let's update our inventory file (/etc/ansible/hosts) for this lesson. Earlier in **"Lesson 16 - Ansible Variables"** lesson for group variable we added both our target nodes to a group called **mygroup**. It's time to split those 2 target nodes in 2 different groups, like below:

```
[mygroup]
target-node1
[othergroup]
target-node2 ansible_host=192.168.56.12 ansible_user=vagrant
```

**1. when**

This can be used where we need to run a tasks on a remote node which satisfies the condition.

Syntax :

```
task:
  - name: <playbook name>
    command: <command to be executed>
    when: <condition>
```

**Playbook Exmaple 1** :

![image](https://drive.google.com/uc?export=view&id=1sy3guLht5HPE0HTv2_5FvvbSERAK8BTg)

**Playbook Exmaple 1 Explanation** : Here in **example-1-when-conditionals.yaml** ansible playbook, we have only 2 tasks defined and task will be run on target nodes based on the condition

**Task 1** : Name of task 1 is **"install package on ubuntu"**. It is using packaging module to install **apach2** but based on the condition. It is using the data stored in ansible facts and checking the **ansible_os_family** variable value to verify the flavour of the OS. In this case it will install **apache2** as target-node1 OS is **ubuntu**.

**Task 2** : Name of task 2 is **install package on centos**. It is also using packaging module to install **httpd** in case OS flavour is RedHat. In our case, this task will be skipped as we have defined only 1 host and it is from Debian family.

**To Run the Playbook** :

```
ansible-playbook example-1-when-conditionals.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1RDrrCN4d3Wux3vtANIEbqggop1BesnSE)

**2. loop and conditionals**

Loop and Conditionals are used when we have to run a task for a given list of items. The task will run against each target node for all the listed items.

Syntax :

```
tasks:
  - name: <playbook name>
    command: <command to be executed>
    loop: <[list of items]>
   when: <condition>
```

**Playbook Exmaple 2** :

![image](https://drive.google.com/uc?export=view&id=16T7rt7v9zc4cLblRkvVHUuCpwXBqw5dM)

**Playbook Exmaple 2 Explanation** : Here in **"example-2-loop-and-conditionals.yaml"** ansible playbook, we have only 1 task which us using loop with conditionals.

**Task 1** : Name of task 1 is **"install git and nginx"**. It is using packaging module to install git and nginx using loop and based on the condition in **all** group.
Here condition is checking the if **inventory_hostname** belongs to **mygroup** or not. If so, then install git and nginx else skip the target node.
**inventory_hostname** is a special variable which takes the hostname from the inventory configuration or the hosts file. In our case inventory hostname is **target-node1** which belongs to **mygroup** and hence git and nginx getting installed only on target-node1 and not on target-node2

**To Run the Playbook** :

```
ansible-playbook example-2-loop-and-conditionals.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1_DuMwsBjALAszjQolvAMgnJiSFub-JUK)

**3. Register Variables with Conditionals**

There could be times when you want to store the output of a task and then based on it, you want to perform another task.

Syntax :

```
tasks:
  - name: <playbook name>
    command: <command to be executed>
    register: <output>
   when: <condition based on register variable>
```

**Playbook Exmaple 3** :

![image](https://drive.google.com/uc?export=view&id=1Sh3GhHKaop0swQ0DKgYLq9klVcoh9vLZ)

**Playbook Exmaple 3 Explanation** : Here in **"example-3-register-with-condition.yamll"** ansible playbook, we have 2 task and the second task is running based on the condition on **all** group.

**Task 1** : Name of task 1 is **"check if vagrant user is present"**. It is using the shell module and running **"ls -lrth /home/ | grep vagrant"** command and storing the output to a register variable called **check_vagrant_user**.

**Task 2** : Name of task 2 is **"print if user is present"**. It is using debug module and printing a message if the user is present.

**Note** : **rc** is the return code which is 0 as **"ls -lrth /home/ | grep vagrant"** command was success in task 1.

**To Run the Playbook** :

```
ansible-playbook example-3-register-with-condition.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1AS-gEuQDqBLSqq8BshLiQgirUtmr0fvg)
