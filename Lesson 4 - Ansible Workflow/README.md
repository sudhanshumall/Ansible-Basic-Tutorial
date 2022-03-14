## Ansible Workflow

![image](https://drive.google.com/uc?export=view&id=1U1B_Mvo9Dwfs1W_hrnJ4C9g11zMSWwGS)

_In the above image, Ansible Management Node is the controlling node which is controlling the entire execution of the playbook. The inventory file provides the list of hosts where the Ansible modules need to be run. The Management Node makes an SSH connection and executes the small modules on the host's machine and install the software._

```
Ansible is a push-based configuration management tool which makes it agentless.

Ansible works by connecting to your target nodes and pushing out the ansible modules to them.

Ansible then executes these modules and remove them once it is finished.
```
