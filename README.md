# Ansible Wordpress

## Requirements

- [Install ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

- You need to have ```two server``` using ```linux on Ubuntu 18.04```.
  - 1 server for your ```mysql database```
  - 1 server for your ```webserver```

## Installation && Configuration

1 - ```git clone git@git.ynov-bordeaux.com:QuentG/ansible_wordpress.git```

2 - Replace with your variables in file ```ansible.cfg``` and files in ```group_vars/```

3 - Launch the playbook : ```ansible-playbook site.yml```

⚠️ The command fail in ```this first launch```... (error python mysql package missing). But if you re-launch the playbook does it work's ! ⚠️

4 - When the ansible task is finished, go to your web host ```http://my-web-ip``` 🔥

PS : To access to the back office the default password is ```admin```.

## Process

- First of all the ```role mysql``` execute.
  - This role install ```mysql``` on server
  - Create a user 
  - Create a database and import the dump

- In a second time the ```role apache-php-ftp``` execute.
  - This role install and configure apache with new vhost
  - Install php
  - Install vsftpd and configure

- To finish the ```role wordpress``` execute.
  - Download a wordpress instance.
  - Extract and move in in the right place ```/var/www/wordpress```
  - Configure connection with database in file ```wp-config.php``` and replace it with the current in ```/var/www/wordpress/wp-config.php```

- It work's ! 🔥