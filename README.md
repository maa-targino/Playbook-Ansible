Playbook-Ansible
================

## 1.0 Introduction:

- This is an Ansible playbook that is used to automate the instalation of a Wordpress application in a localhost server. 
- For this procedure we will use the local user to require the installation.

### 1.1 Add root permissions to a local user:
#### 1.1.1 Access the sudoers folder with this command line:
user@ubuntu:~$ sudo visudo
#### 1.1.2 Go to *#User privilege specification* section;
#### 1.1.3 Under the previous line add the following instructions:
user  ALL=(ALL:ALL) NOPASSWD: ALL

## 2.0 Deployment requirements:
- **SSH Server**
- **Ansible**

### 2.1 SSH server installation:

#### 2.1.1 SSH server installation command line:
sudo apt-get install openssh-server

#### 2.1.2 Edit root user permitions to access the SSH server:
user@ubuntu:~$ sudo gedit etc/ssh/sshd_config

####

#### 2.1.3 

### 2.2 Ansible Installation:

## 3.0 



