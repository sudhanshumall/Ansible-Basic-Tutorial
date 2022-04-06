## Ansible Modules

- Ansible modules are reusable, standalone scripts that can be used by the Ansible API, or by the ansible or Ansible playbook, which gets executed either locally or remotely on the target nodes

- Ansible modules are pushed to the target nodes when we run an Ansible playbook

- They return information to ansible by printing a JSON string to stdout before exiting

**Ansible Modules List** : https://docs.ansible.com/ansible/2.9/modules/modules_by_category.html

Before we go deep into Ansible Modules, lets also create our custom inventory file with the target nodes we created in **"Lesson 8 - Ansible Inventory Format"**

**Steps to create custom inventory file**

1. Create a inventory file

```
touch my-inventory
```

2. Paste below target node details in the new inventory file i.e "my-inventory"

```
target-node1 ansible_host=192.168.56.11 ansible_user=vagrant
target-node2 ansible_host=192.168.56.12 ansible_user=vagrant
```

_**Note** : I have added custom inventory file in this lesson. Also make sure to use the IP you used while creating the VM using vagrant_

_Now let's see some of the modules with real time examples :_

**1. Commands Modules**

```
    command     : Execute commands on target nodes
    script      : Execute local scripts on remote/target nodes
    shell       : Execute shell commands on target nodes, it is almost like the command module but runs the command through a shell (/bin/sh) on the target remote node
```

**Playbook Exmaple 1** :

![image](https://drive.google.com/uc?export=view&id=1AeaB4NwbsrWfsHwISBFHurR-FuFYoc-t)

**Playbook Exmaple 1 Explanation** : Here in **example-1-commands-modules.yaml** ansible playbook we have used 4 tasks, running on **all** group

**Task 1** : Name of task 1 is **"list the files"**. It is using **"command module"** and listing the files under **/home/vagrant/** directory on all the target nodes we have in our custom inventory file.

**Task 2** : Name of task 2 is **"run the script on target node"**. It is using **script** module to run the **example-1-script.sh** on all the target nodes we have in our custom inventory file. You don't need to copy **example-1-script.sh** script on the target node because it is the **script** module which takes care of it. It internally transfers the script to the target nodes and executes it.

**Task 3** : Name of task 3 is **"copy example-1-script.sh to remote machine for next task"**. It is using **file** module (which is not the part of **command** module) to copy the script on the target nodes, so that the next task which is using **shell** module can execute the script.

**Task 4** : Name of task 4 is **"execute shell command"**. It is using **shell** module to execute the script.

_**Note** : Difference between **script** and **shell** command module is that, when using **script** module, you don't need to copy the script to the remote machine, however in case of **shell** module, you need to copy the script first to the target nodes (hence **task 3** is required) in case of **shell** module_

**To Run the Playbook** : ansible-playbook -i my-inventory example-1-commands-modules.yaml

**Output** :

![image](https://drive.google.com/uc?export=view&id=1Bl_3nyehuqbwo7Ah7Il1lofHE26cqgmN)

**2. Files Modules**

```
    fetch       : Fetches the file from target node to local machine
    file        : Manages files and its properties
    find        : Returns files based on defined criteria
    lineinfile  : Manages lines in the file
    blockinfile : insert/update/remove block of texts
```

**Playbook Exmaple 2** :

![image](https://drive.google.com/uc?export=view&id=1DaaA2wqC-g-t4FOlK8cr4gIii61BB7uM)

**Playbook Exmaple 2 Explanation** : Here in **example-2-files-modules.yaml** ansible playbook we have used 7 tasks, running on **target-node1** and **target-node2** group. Check the host section, another way to define when you have multiple target nodes.

**Task 1** : Name of task 1 is **"fetch the file from remote/target machine"**. It is using **fetch** module and t is copying the file from remote node to local machine from where you are running the playbook.

**Task 2** : Name of task 2 is **"change file ownership, group and its permission"**. It is using **file** module and changing the ownership, group and file permission of **example-1-script.log** file which was created in **example-1-commands-modules.yaml** playbook. Also, notice that we have used **become** keyword only for this task as this task requires root provileges for changing the ownsership, group and permission of the file.

**Task 3** : Name of task 3 is **"find files older than 2 days"**. It is using **find** module and getting the list of files older than 2 days in /home/vagrant directory.
As of now this doesn't print the list of files and we will see in Ansible Variables lesson on how to acheive that.

**Task 4** : Name of task 4 is **"create an empty file for lineinfile module example"**. It is using **file** module and creating an empty file i.e. **lineinfile.txt** in /home/vagrant directory.

**Task 5** : Name of task 5 is **"create an empty file for blockinfile module example"**. It is using **file** module and creating an empty file i.e. **blockinfile.txt** in /home/vagrant directory.

**Task 6** : Name of task 6 is **"insert a line in file"**. It is using **lineinfile** module and making sure mentioned line is present in the **lineinfile.txt** file.

**task 7** : Name of task 7 is **"insert or update block of lines in a file"**. It is using **blockinfile** module and making sure mentioned blocks of lines are present in **blockinfile.txt** file.

_**Note** : Task 4 and 5 both are common and creating an empty file. We will see in future lesson on how we can improve this using loop_

**To Run the Playbook** : ansible-playbook -i my-inventory example-2-files-modules.yaml

**Output** :

![image](https://drive.google.com/uc?export=view&id=1F7j_D2qt5d19AKfAoixQi2HwPxHg2dYn)

**3. Packaging Modules**

```
    apt         : manages apt packages
```

**Playbook Exmaple 3** :

![image](https://drive.google.com/uc?export=view&id=1uc7AMw3jhK98-LLZxc609LMYLEY4aani)

**Playbook Exmaple 3 Explanation** : Here in **example-3-packaging-module.yaml** ansible playbook, we have used 2 tasks and running only on target-node1. Also, we have used **become** keyword because packaging module requires root provileges for installing any packages.

**Task 1** : Name of task 1 is **"install git"**. It is using **apt** module and installing git (using state as **present**) on target-node1.

**Task 2** : Name of task 2 is **"uninstall apache2"**, which we installed in **"Lesson 12 - Ansible Ad-hoc Commands"**. It is using **apt** module and uninstalling apache2 (using state as **absent**) on target-node1.

**Task 3** : Name of task 3 is **"install nginx"**. It is also using **apt** module and installing nginx (using state as **present**) on target-node1.

**To Run the Playbook** : ansible-playbook -i my-inventory example-3-packaging-module.yaml

**Output** :

![image](https://drive.google.com/uc?export=view&id=1mQVzbeFsGtjpDGEToOeBmFEli7mj0eMO)

**4. System Modules**

```
    ping        : tries to connect to remote host and returns pong on connecting successfully
    service     : controls state of services
    cron        : manage crontab entires
    group       : add or remove groups
    user        : manage user accounts
    reboot      : reboot target machine
```

**Playbook Exmaple 4** :

![image](https://drive.google.com/uc?export=view&id=1eF8PN7YyLxDpqbb7cH4ptLcAYI2yHHJk)

**Playbook Exmaple 4 Explanation** : Here in **example-4-system-modules.yaml** ansible playbook, we have used 6 tasks and running only on target-node1.

**Task 1** : Name of task 1 is **"test remote host connection"**. It is using **ping** module to check the connectivity between Ansible Controller machine and target node machine.

**Task 2** : Name of task 2 is **"make sure nginx is running"**. It is using **service** module and making sure that the nginx we installed previous playbook is up and running.
In this, the **state** which is mentioned as **started** ensures that nginx is running and it only starts nginx if not running.

**Task 3** : Name of task 3 is **"setup cron"**. It i using **cron** module and setting up a cron we defined in the task.

**Task 4** : Name of task 4 is **"add a new group"**. It is using **group** module to create a new group in the target machine.

**Task 5** : Name of task 5 is **"add a new user"**. It is using **user** module and creating a new user.

**Task 6** : Name of task 6 is **"reboot machine"**. It is using **reboot** module and will reboot your target node which in our case is target-node1.

**To Run the Playbook** : ansible-playbook -i my-inventory example-4-system-modules.yaml

**Output** :

![image](https://drive.google.com/uc?export=view&id=1vzLPIXAGAmxkm8UgOQsrqATXxt4PBCWq)

**5. Source Control Modules**

```
    git         : manages git repository checkouts to deploy the files
```

**Playbook Exmaple 5** :

![image](https://drive.google.com/uc?export=view&id=1cIZh7K106Fa4vXmAk-stxj3QlKAgPfiq)

**Playbook Exmaple 5 Explanation** : Here in **example-5-source-control-modules.yaml** ansible playbook, we have only 1 task and running only on target-node1.

**Task 1** : Name of task 1 is **"clone git repo"** and is using **git** module. Here this task will create a new directory called **ansible-playbooks** and clone the contents of the repo which we are cloning.

**To Run the Playbook** : ansible-playbook -i my-inventory example-5-source-control-modules.yaml

**Output** :

![image](https://drive.google.com/uc?export=view&id=1O-AHjcVgFuzCesPZW39o3hr2frmszvFn)

**6. Cloud Modules**

```
Ansible Cloud module works with multiple cloud providers like AWS, GCP, Azure, Digital Ocean, Hetzner Cloud etc....
```

and many more modules
