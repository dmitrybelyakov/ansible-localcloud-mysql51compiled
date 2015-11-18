localcloud-mysql51compiled
=========

This role is created for legacy systems that need MySQL 5.1 and since it's not available from official repositories it will compile it from sourcecode.
Upon installation will provide functionality to manage users and remote access iun the same way [localcloud-mysql](https://github.com/dmitrybelyakov/ansible-localcloud-mysql) does.

Requirements
------------

This role requires an Ubuntu Box. It was tested on 12 (precise) LTS release.

Dependencies
------------

This role has no dependencies.


Role Variables
--------------

`mysql_root_password` - required. Set your root password. You can also use this setting to update your password.

`mysql_packages` - optional. A list of packages to install for mysql support. Defaults 'mysql-server' and 'mysql-client' available from official repositories. But you can override this. For example on Ubuntu trusty you can use 'mysql-server-5.6' and 'mysql-client-5.6' packages instead.

`mysql_bind_address` - optional. Address to bind to. Defaults to local connections from 127.0.0.1.

`mysql_port` - optional. Port to listen for connections on. Defaults to standard 3306.

`firewall_open` - optional. Whether to open TCP connections to certain ports on the firewall. Disabled by default. This option together with mysql_users allows you to enable remote connections.

`mysql_users` - optional. A dictionary of users and their connection credentials and privileges. Use this to create users as well as enable remote access. A simple user definition can look like this:

```yml
mysql_users:
  username:
    host: '%'
    password: 'password'
    privileges: '*.*:ALL,GRANT'
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
- hosts: servers
  roles:
     - localcloud-php
  vars:
    mysql_root_password: god
```

License
-------

MIT

