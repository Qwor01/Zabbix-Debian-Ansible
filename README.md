# 🚦 Playbook Ansible to deploy Zabbix in Debian 

---

> [!IMPORTANT]  
> This playbooks is designed to deploy zabbix into three separate VMs (One for the front-end, one for the back-end, one for the DB)
> Requirements:
>   - ssh installed on the VMs
>   - python installed on the VMs
>   - ansible installed on the machine which will run the playbook

---

####  **Configuring the Inventory and Vars Files**

In the vars.yaml file:

```vars.yaml
---
zabbix_server_version: "7.0"
zabbix_front_host: xxx.xxx.xxx.xxx 
zabbix_db_host: xxx.xxx.xxx.xxx     
zabbix_server_host: xxx.xxx.xxx.xxx 
zabbix_db_name: "zabbix"
zabbix_db_user: zabbix
mariadb_root_password: dbPassword
zabbix_db_password: zabbixPassword
```

Replace the x with the actual IPs from your machines, and set up your own mariadb root password, zabbix db user and zabbix db password. You may also change the zabbix version to be used.

In the inventory.ini file:


```inventory.ini
[ZabbixServer]
ZabbixServerVM ansible_host=xxx.xxx.xxx.xxx  ansible_user=user ansible_ssh_private_key_file=~/.ssh/ansible_key

[ZabbixFront]
ZabbixFront ansible_host=xxx.xxx.xxx.xxx  ansible_user=user ansible_ssh_private_key_file=~/.ssh/ansible_key

[ZabbixDB]
ZabbixDB ansible_host=xxx.xxx.xxx.xxx  ansible_user=user ansible_ssh_private_key_file=~/.ssh/ansible_key
```
Replace the x with the actual IPs from your machines, user with you actual VM user and the SSH key path to the path of your actual private key for connecting to the VMs
---

####  **Running the playbook**

To run the playbook simply use:

```bash
ansible-playbook -i inventory.ini install_server.yaml -kKinventory.ini
```

```bash
ansible-playbook -i inventory.ini install_front.yaml -kKinventory.ini
```

```bash
ansible-playbook -i inventory.ini install_db.yaml -kKinventory.ini
```

From the root directory of the project, after running this commands you'll be prompted to enter an SSH password which ansible will use to run root commands, so make sure your user defined in your inventory.ini is in the sudoers group of your VM# 🚦 Playbook Ansible de despliegue de Zabbix en Debian **

---

> [!IMPORTANT]  
> This playbooks is designed to deploy zabbix into three separate VMs (One for the front-end, one for the back-end, one for the DB)
> Requirements:
>   - ssh installed on the VMs
>   - python installed on the VMs
>   - ansible installed on the machine which will run the playbook

---

####  **Configuring the Inventory and Vars Files**

In the vars.yaml file:

```vars.yaml
---
zabbix_server_version: "7.0"
zabbix_front_host: xxx.xxx.xxx.xxx 
zabbix_db_host: xxx.xxx.xxx.xxx     
zabbix_server_host: xxx.xxx.xxx.xxx 
zabbix_db_name: "zabbix"
zabbix_db_user: zabbix
mariadb_root_password: dbPassword
zabbix_db_password: zabbixPassword
```

Replace the x with the actual IPs from your machines, and set up your own mariadb root password, zabbix db user and zabbix db password. You may also change the zabbix version to be used.

In the inventory.ini file:


```inventory.ini
[ZabbixServer]
ZabbixServerVM ansible_host=xxx.xxx.xxx.xxx  ansible_user=user ansible_ssh_private_key_file=~/.ssh/ansible_key

[ZabbixFront]
ZabbixFront ansible_host=xxx.xxx.xxx.xxx  ansible_user=user ansible_ssh_private_key_file=~/.ssh/ansible_key

[ZabbixDB]
ZabbixDB ansible_host=xxx.xxx.xxx.xxx  ansible_user=user ansible_ssh_private_key_file=~/.ssh/ansible_key
```


Replace the x with the actual IPs from your machines, user with you actual VM user and the SSH key path to the path of your actual private key for connecting to the VMs

---

####  **Running the playbook**

To run the playbook simply use:

```bash
ansible-playbook -i inventory.ini install_server.yaml -kKinventory.ini
```

```bash
ansible-playbook -i inventory.ini install_front.yaml -kKinventory.ini
```

```bash
ansible-playbook -i inventory.ini install_db.yaml -kKinventory.ini
```

From the root directory of the project, after running this commands you'll be prompted to enter an SSH password which ansible will use to run root commands, so make sure your user defined in your inventory.ini is in the sudoers group of your VM
