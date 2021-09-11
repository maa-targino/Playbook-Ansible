Ansible playbook deployment
==========================

## 1.0 Introduction:

- This is an Ansible playbook that is used to automate the instalation of a Wordpress application in a localhost server. 
- For this procedure we will use the local user to require the installation.

### 1.1 Add root permissions to a local user:
#### 1.1.1 Access the sudoers folder with this command line:
user@ubuntu:~$ sudo visudo
#### 1.1.2 Go to *User privilege specification* section;
#### 1.1.3 Under the previous line add the following instructions:
user  ALL=(ALL:ALL) NOPASSWD: ALL

## 2.0 Deployment requirements:
- **SSH Server**
- **Ansible**

### 2.1 SSH server installation:

#### 2.1.1 SSH server installation command line:
user@ubuntu:~$ sudo apt-get install openssh-server

#### 2.1.2 Edit root user permitions to access the SSH server:
user@ubuntu:~$ sudo gedit etc/ssh/sshd_config

#### 2.1.3 Uncomment the *#PermitRootLogin yes* this way:
PermitRootLogin yes

#### 2.1.4 Restart the SSH server:
user@ubuntu:~$ service ssh restart
user@ubuntu:~$ service ssh status

#### 2.1.5 Generate new SSH keys:
user@ubuntu:~$ ssh-keygen

#### 2.1.6 Copy the new SSH key to the authorized keys path with the following command line:
user@ubuntu:~$ cp -p ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys

### 2.2 Ansible installation:

#### 2.2.1 Add a new repository for Ansible:
user@ubuntu:~$ sudo apt-add-repository ppa:ansible/ansible

#### 2.2.2 After that all you need is accept the keys and to press *<*ENTER*>* when the system requires.

#### 2.2.3 Update the apt-get with the following command line:
user@ubuntu:~$ sudo apt-get update

#### 2.2.4 Ansible installation command line:
user@ubuntu:~$ sudo apt-get install ansible

## 3.0 GitHub requirements:
- **Git**
- **Repository**

### 3.1 Git installation:

#### 3.1.1 Check Git version:
user@ubuntu:~$ git --version

#### 3.1.2 Installation command line:
user@ubuntu:~$ sudo apt install git-all






