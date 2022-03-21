## Lab Setup using Oracle Virtual Box and Vagrant

![image](https://drive.google.com/uc?export=view&id=1za9mqAB8ICgKQIXh_5fOZMxr2UE92gYW)

- Download Oracle Virtual Box from https://www.virtualbox.org/wiki/Downloads

- For Windows Users – Enable virtulization https://www.tutorialspoint.com/windows10/windows10_virtualization.htm

- Download Vagrant from https://www.vagrantup.com/downloads

**Steps to create VM using Vagrant**

1. Create some folder where you want to keep your vagrant files

```
mkdir -p ~/vagrant/vm1
```

2. cd to the new directory, created above

```
cd ~/vagrant/vm1
```

3. Initialize the directory to be a Vagrant environment by creating an initial Vagrantfile

```
vagrant init ubuntu/bionic64
```

_Note : https://app.vagrantup.com/boxes/search (you can pick any other vagrant boxes as well if not comfortable with Ubuntu)_

4. Replace Vagrantfile created using above step with below content

```
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network :private_network, ip: "192.168.56.12"
  config.vm.network "forwarded_port", guest: 22, host: 2222
end
```

5. Bring up the VM

```
vagrant up
```

Note : vagrant halt - for stoping the VM

6. SSH to the VM using vagrant command

```
vagrant ssh
```

6. Repeat the same step if you need 1 more VM (use another IP)

**Passwordless SSH to VM**
Note : Below steps can also be done if you are using any cloud provider machines (AWS EC2 or Azure VM)

1. Create authentication ssh-keygen keys on you localhost where Ansible is installed

```
ssh-keygen
```

Note: Keep pressing "Enter" button

2. Above command will generate the keys (public and private) inside ~/.ssh/ folder with default name as "id_rsa" and "id_rsa.pub"

3. Copy the content of "id_rsa.pub" file and paste it inside the VM under "~/.ssh/authorized_keys" (do not delete the existing key)

4. Now you should be able to use ssh command to connect to the VM

```
ssh vagrant@192.168.56.12
```
