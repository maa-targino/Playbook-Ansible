Ansible playbook deployment
==========================

## 1. Introduction:

This is an Ansible playbook that is used to automate the installation of a Wordpress application in a localhost server.  
For this procedure we will use an Ubuntu client, with the local user, to require the installation.

### 1.1 Add root permissions to a local user:
#### 1.1.1 Access the sudoers folder with this command line:

>user@ubuntu:~$ sudo visudo

#### 1.1.2 Go to *User privilege specification* file section;

>#User privilege specification yes  
root  ALL=(ALL>ALL) ALL

#### 1.1.3 Add the following instructions just below the previous line:

>user  ALL=(ALL:ALL) NOPASSWD: ALL

## 2. Deployment requirements:

- **SSH Server**
- **Ansible**

### 2.1 SSH server installation:

#### 2.1.1 SSH server installation command line:

>user@ubuntu:~$ sudo apt-get install openssh-server

#### 2.1.2 Edit root user permitions to access the SSH server:

>user@ubuntu:~$ sudo gedit etc/ssh/sshd_config

#### 2.1.3 Uncomment the *#PermitRootLogin yes* this way:

>PermitRootLogin yes

#### 2.1.4 Restart the SSH server:

>user@ubuntu:~$ service ssh restart

#### 2.1.5 Generate new SSH keys:

>user@ubuntu:~$ ssh-keygen

#### 2.1.6 Copy the new SSH key to the authorized keys path with the following command line:

>user@ubuntu:~$ cp -p ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys

### 2.2 Ansible installation:

#### 2.2.1 Add a new repository for Ansible:

>user@ubuntu:~$ sudo apt-add-repository ppa:ansible/ansible

#### 2.2.2 After that all you need is accept the keys and to press < ENTER > when the system requires.

#### 2.2.3 Update the apt-get with the following command line:

>user@ubuntu:~$ sudo apt-get update

#### 2.2.4 Ansible installation command line:

>user@ubuntu:~$ sudo apt-get install ansible

#### 2.2.5 Check Ansible version:

>user@ubuntu:~$ ansible --version

## 3. Playbook deployment:

### 3.1 Creating the hosts and plyabook.yml files:

#### 3.1.1 Create a folder to store the playbook files:

>user@ubuntu:~$ mkdir folder-name

#### 3.1.2 Create the hosts file in the folder:

>user@ubuntu:~$ cd folder-name 
> 
>user@ubuntu:~/folder-name$ touch hosts

#### 3.1.3 Open the hosts file:

>user@ubuntu:~/folder-name$ sudo gedit hosts

#### 3.1.4 Click on the following link and copy the content to your hosts file:

**[Hosts](https://github.com/maa-targino/Playbook-Ansible/blob/master/hosts)**

#### 3.1.5 Create playbook.yml file in the same folder:

>user@ubuntu:~$ cd folder-name

>user@ubuntu:~/folder-name$ touch playbook.yml

#### 3.1.6 Click on the following link and copy the content to your playbook.yml file:

**[Playbook](https://github.com/maa-targino/Playbook-Ansible/blob/master/playbook.yml)**

### 3.2 Creating the playbook roles:

- **server**
- **php**
- **mysql**
- **wordpress**

#### 3.2.1 Create the roles in the folder with the Ansible Galaxy collection:

>user@ubuntu:~/folder-name$ ansible-galaxy init server  
>
>user@ubuntu:~/folder-name$ ansible-galaxy init php  
>
>user@ubuntu:~/folder-name$ ansible-galaxy init mysql  
>
>user@ubuntu:~/folder-name$ ansible-galaxy init wordpress  

### 3.3 Edit the files in the roles folder:

#### 3.3.1 Go to the roles folder:

>user@ubuntu:~/folder-name$ cd roles

#### 3.3.2 Click on the link and copy the content to the file in the following path: *server/tasks/main.yml*

**[Server/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/server/tasks/main.yml)**  

>user@ubuntu:~/folder-name/roles$ gedit server/tasks/main.yml

#### 3.3.3 Click on the link and copy the content to the file in the following path: *php/tasks/main.yml*

**[PHP/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/php/tasks/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit php/tasks/main.yml

#### 3.3.4 Click on the link and copy the content to the file in the following path: *mysql/tasks/main.yml*

**[MySQL/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/mysql/tasks/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit mysql/tasks/main.yml

#### 3.3.6 Click on the link and copy the content to the file int following path: *mysql/defaults/main.yml*

**[MySQL/Defaults](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/mysql/defaults/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit mysql/defaults/main.yml

#### 3.3.5 Click on the link and copy the content to the file in the following path: *wordpress/tasks/main.yml*

**[Wordpress/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/wordpress/tasks/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit wordpress/tasks/main.yml

#### 3.3.6 Click on the link and copy the content to the file in the following path: *wordpress/handlers/main.yml*

**[Wordpress/Handlers](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/wordpress/handlers/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit wordpress/handlers/main.yml

## 4. GitHub requirements:

- **Git**
- **Repository**

### 4.1 Git installation:

#### 4.1.1 Check Git version:

>user@ubuntu:~$ git --version

#### 4.1.2 Installation command line:

>user@ubuntu:~$ sudo apt install git-all

### 4.2 GitHub repository:

#### 4.2.1 Click on the link to create a new repository on GitHub:

**[Create a new repository](https://github.com/new)**

#### 4.2.2 Click on the following link to create a new personal access token:

**[Generate new token](https://github.com/settings/tokens/new)**

#### 4.2.3 Commit and push the files to GitHub repository:

>user@ubuntu:~$ git init  
>
>user@ubuntu:~$ git add .  
>
>user@ubuntu:~$ git commit -m "first commit"  
>
>user@ubuntu:~$ git remote add origin https://github.com/your-username/your-repo-name.git  
>
>user@ubuntu:~$ git push -u origin master  

4.2.4 Enter with your GitHub username:

>Username for 'https://github.com': your-username  

4.2.5 Enter with your GitHub personal access token:

>Password for 'your-username@github.com': your-token  

## Research sources:

- [Basic Syntax | Markdown Guide](https://www.markdownguide.org/basic-syntax/)
- [Git - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Editing files -GitHub Docs](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files#editing-files-in-your-repository)




