## ansible mariadb
deploy mariadb or galera by ansible 1.7.2 or ansible 2.1, support ubuntu and centos.

### before deploy
* edit inventory file <code>inventory/mariadb_hosts</code>

```
# multiple node for cluster
[mariadb_nodes]
192.168.33.33
192.168.33.34
192.168.33.35

# or single node
[mariadb_nodes]
192.168.33.33

```

### run it

* provision in development environment:

```
# install
ansible-playbook -i inventory/mariadb_hosts mariadb_install.yml \
-e "ansible_ssh_user=willyhu ansible_ssh_pass=secret ansible_sudo_pass=secret" \
-e "install_mode=install"

# configure
ansible-playbook -i hosts/mariadb_hosts mariadb_install.yml \
-e "ansible_ssh_user=willyhu ansible_ssh_pass=secret ansible_sudo_pass=secret" \
-e "install_mode=config"
```

### variables and default value
there are some variables and default value that you can change. Just pass as an extra variable when you execute ansible-playbook or you can also update these variables by edit <code>vars/mariadb.yml</code> before start to deploy.

* install_mode: <code>install</code> (install | config)
* listen_nic: <code>eth0</code>
* db_passwd: <code>password</code>
* db_listen_port: <code>3306</code>
