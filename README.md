Implementação de uma playbook Ansible
=====================================

![Ansible-logo](https://github.com/maa-targino/Playbook-Ansible/blob/master/ansible-logo.png)

## 1. Introdução:

Esta é uma playbook Ansible utilizada para automatizar a instalação de uma aplicação Wordpress em um servidor localhost.  
Foi utilizado neste procedimento um servidor de SSH e um cliente Ubuntu para as requisições. Foi utiizado também o usuário local do Ubuntu. 

### 1.1 Adicionar permissões de root a um usuário local:
#### 1.1.1 Acesse a pasta sudoers com o seguinte comando:

>user@ubuntu:~$ sudo visudo

#### 1.1.2 Vá para a seção *User privilege specification*;

>#User privilege specification  
root  ALL=(ALL:ALL) ALL

#### 1.1.3 Adicione a seguinte instrução logo abaixo das linhas anteriores:

>user  ALL=(ALL:ALL) NOPASSWD: ALL

## 2. Requerimentos para a implantação:

- **Servidor SSH instalado**
- **Ansible instalado**

### 2.1 Instalação do servidor de SSH:

#### 2.1.1 Faça a instalação do servidor de SSH:

>user@ubuntu:~$ sudo apt-get install openssh-server

#### 2.1.2 Altere as permissões de root para o acesso do servidor de SSH:

>user@ubuntu:~$ sudo gedit etc/ssh/sshd_config

#### 2.1.3 Descomente a linha *#PermitRootLogin yes* deste modo:

>PermitRootLogin yes

#### 2.1.4 Reinicie o servidor de SSH:

>user@ubuntu:~$ service ssh restart

#### 2.1.5 Gere uma nova chave SSH:

>user@ubuntu:~$ ssh-keygen

#### 2.1.6 Copie a nova chave SSH com o seguinte comando:

>user@ubuntu:~$ cp -p ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys

### 2.2 Instalação do Ansible:

#### 2.2.1 Crie um novo repositório Ansible:

>user@ubuntu:~$ sudo apt-add-repository ppa:ansible/ansible

#### 2.2.2 Depois disso, pressione < ENTER > sempre que o sistema solicitar.

#### 2.2.3 Atualize o apt-get com o seguinte comando:

>user@ubuntu:~$ sudo apt-get update

#### 2.2.4 Faça a instalação do Ansible:

>user@ubuntu:~$ sudo apt-get install ansible

#### 2.2.5 Verifique a versão e confirme se o Ansible foi instalado corretamente:

>user@ubuntu:~$ ansible --version

## 3. Implementação da playbook:

### 3.1 Criando os arquivos da playbook:

#### 3.1.1 Crie uma pasta para armazenar os arquivos:

>user@ubuntu:~$ mkdir folder-name

#### 3.1.2 Crie o arquivo 'hosts' dentro da pasta:

>user@ubuntu:~$ cd folder-name 
> 
>user@ubuntu:~/folder-name$ touch hosts

#### 3.1.3 Abra o arquivo 'hosts' com o editor de textos:

>user@ubuntu:~/folder-name$ sudo gedit hosts

#### 3.1.4 Clique no link a seguir e copie seu conteúdo para dentro do seu arquivo 'hosts':

**[Hosts](https://github.com/maa-targino/Playbook-Ansible/blob/master/hosts)**

#### 3.1.5 Crie o arquivo 'playbook.yml' dentro da mesma pasta:

>user@ubuntu:~$ cd folder-name

>user@ubuntu:~/folder-name$ touch playbook.yml

#### 3.1.6 Abra o arquivo 'playbook.yml' com o editor de textos:

>user@ubuntu:~/folder-name$ sudo gedit playbook.yml

#### 3.1.7 Clique no link a seguir e copie seu conteúdo para dentro do seu arquivo 'playbook.yml':

**[Playbook](https://github.com/maa-targino/Playbook-Ansible/blob/master/playbook.yml)**

### 3.2 Criação das roles:

- **server**
- **php**
- **mysql**
- **wordpress**

#### 3.2.1 Crieas roles dentro da pasta utilizando a coleção Ansible Galaxy:

>user@ubuntu:~/folder-name$ ansible-galaxy init server  
>
>user@ubuntu:~/folder-name$ ansible-galaxy init php  
>
>user@ubuntu:~/folder-name$ ansible-galaxy init mysql  
>
>user@ubuntu:~/folder-name$ ansible-galaxy init wordpress  

### 3.3 Altere os arquivos dentro da pasta 'roles':

#### 3.3.1 Vá para o caminho da pasta 'roles':

>user@ubuntu:~/folder-name$ cd roles

#### 3.3.2 Clique no link a seguir e copie seu conteúdo para o seguinte caminho: *server/tasks/main.yml*

**[Server/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/server/tasks/main.yml)**  

>user@ubuntu:~/folder-name/roles$ gedit server/tasks/main.yml

#### 3.3.3 Clique no link a seguir e copie seu conteúdo para o seguinte caminho: *php/tasks/main.yml*

**[PHP/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/php/tasks/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit php/tasks/main.yml

#### 3.3.4 Clique no link a seguir e copie seu conteúdo para o seguinte caminho: *mysql/tasks/main.yml*

**[MySQL/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/mysql/tasks/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit mysql/tasks/main.yml

#### 3.3.6 Clique no link a seguir e copie seu conteúdo para o seguinte caminho: *mysql/defaults/main.yml*

**[MySQL/Defaults](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/mysql/defaults/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit mysql/defaults/main.yml

#### 3.3.5 Clique no link a seguir e copie seu conteúdo para o seguinte caminho: *wordpress/tasks/main.yml*

**[Wordpress/Tasks](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/wordpress/tasks/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit wordpress/tasks/main.yml

#### 3.3.6 Clique no link a seguir e copie seu conteúdo para o seguinte caminho: *wordpress/handlers/main.yml*

**[Wordpress/Handlers](https://github.com/maa-targino/Playbook-Ansible/blob/master/roles/wordpress/handlers/main.yml)**

>user@ubuntu:~/folder-name/roles$ gedit wordpress/handlers/main.yml

## 4. Requerimentos do GitHub:

- **Git instalado**
- **Um repositório**

### 4.1 Instalação do Git:

#### 4.1.1 Verifique a versão do Git e se ele já está instalado:

>user@ubuntu:~$ git --version

#### 4.1.2 Comando para instalar o Git:

>user@ubuntu:~$ sudo apt install git-all

### 4.2 Repositório no GitHub:

#### 4.2.1 Clique no link para criar um novo repositório no GitHub:

**[Create a new repository](https://github.com/new)**

#### 4.2.2 Clique no link para criar um novo token de acesso pessoal do GitHub:

**[Generate new token](https://github.com/settings/tokens/new)**

#### 4.2.3 Commit e dê push nos arquivos para o seu repositório no GitHub:

>user@ubuntu:~$ git init  
>
>user@ubuntu:~$ git add .  
>
>user@ubuntu:~$ git commit -m "first commit"  
>
>user@ubuntu:~$ git remote add origin https://github.com/your-username/your-repo-name.git  
>
>user@ubuntu:~$ git push -u origin master  

#### 4.2.4 Entre com o seu nome do usuário do GitHub:

>Username for 'https://github.com': your-username  

#### 4.2.5 Entre com o seu novo token de acesso pessoal do GitHub:

>Password for 'your-username@github.com': your-token  

## Fontes de consulta:

- [Editing files -GitHub Docs](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files#editing-files-in-your-repository)
- [Basic Syntax | Markdown Guide](https://www.markdownguide.org/basic-syntax/)
- [Git - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)





