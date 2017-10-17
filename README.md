Role of installing MySQL
=========

MySQL ansible galaxy role.

Requirements
------------

None

Role Variables
--------------

* mysql_version  
install MySQL version

* mysql_port  
run port

* mysql_character_set  
default character set

* mysql_timezone
default timezone

* mysql_lower_case_table_names  
lower_case_table_names property

* mysql_password_expire  
password expire

* mysql_secure_file_priv_path  
secure_file_priv setting  
If set empty then disable secure_file_priv

* mysql_max_allowed_packet  
max allowed packet size

* mysql_max_connections  
max connections

* mysql_enable_query_log  
If set `True` then enable this

* mysql_enable_query_log_path  
If mysql_enable_query_log set `True` need set this

* mysql_enable_slow_query  
If set `True` then enable this

* mysql_enable_slow_query_path    
If mysql_enable_query_log set `True` need set this

* mysql_root_password  
root user password

* mysql_databases
create databases

* mysql_users  
add users

Dependencies
------------

None

Example Playbook
----------------

```yml
---
- hosts: all
  become: true
  roles:
    - role: galaxy-mysql
      mysql_databases:
        - db1
        - db2
      mysql_users:
        - user: user1
          password: ":GNpHUG6w1%u"
          priv: "*.*:ALL"
```

And run vault managed playbook.  
```yml
$ANSIBLE_VAULT;1.1;AES256
33613039386336353433633232623037396665303138383264653531303962363938333163373430
3732383836613265326138396631363333356433666364380a663938613838326461343162646638
30346232666163613338383766366634353037663438643132626265376565623161363530663166
3861326139623835330a373430303432396261656230633035393262333632653537653536616133
39663838333431633365313365633466346139636665346562656635363632323633613639333937
31316237653039323438623663346638396236376564393535366664386236613664353231643863
393332396330306461376639313965636161
```

```bash
ansible-playbook -i hosts playbook.yml --extra-vars="@secrets.yml" --vault-password-file=.password
```

License
-------

BSD

Author Information
------------------

[Daisuke Maeda](https://github.com/dmae3 "Daisuke Maeda")
