## Ansible Loops

Ansible Loop is used to repeat any task which needs to be triggered multiple times in an Ansible playbook.

Use case - Creating/Deleting multiple files, creating/Deleting multiple users, Installing multiple packages using apt or yum

**Playbook Exmaple 1** :

Suppose we have to create 3 files, let's see how we can create it without using loop

![image](https://drive.google.com/uc?export=view&id=1wkwT6oDLlEv4M9rrzakHJGw0DxBC7FZE)

**Playbook Exmaple 1 Explanation** : Here in **example-1-create-file-without-loop.yaml** ansible playbook, we have created 3 different task for creating 3 different empty files.

**To Run the Playbook** :

```
ansible-playbook example-1-create-file-without-loop.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1korvaV9c2zzNneuGzXOEUqLKC18vVxAM)

**Note** : You can see in **Playbook Exmaple 1**, we have repetitive code for same task, now let's make use of ansible loops and write an asnible playbook to delete these three files using ansible loop directive

**Playbook Exmaple 1** :

![image](https://drive.google.com/uc?export=view&id=1GbqQiZD6UzX2S9FU_S3dmzjcDqqA8XMV)

**Playbook Exmaple 1 Explanation** : Here in **example-2-delete-file-with-loop.yaml** ansible playbook, now instead of 3 different tasks we have only 1 task and using loop directive.

**Task 1** : Name of task 1 is **"delete three empty files"** and instead of using 3 different task for same work, now we are using loop directive and acheiving the same work in just 1 task. Here the loop directive executes the same task multiple times and stores the value of each item in a variable called **item**.

**To Run the Playbook** :

```
ansible-playbook example-2-delete-file-with-loop.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=13o_3xBWPO9dPZhJfI5xj1P_KTFUO1rBh)
