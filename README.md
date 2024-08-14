Nginx
=========

Nginx Debian installer for load balancing.

Tested on OS Debian GNU/Linux 12 (bookworm) with kernel Linux 6.1.0-23-amd64.

Install
-------
```
ansible-galaxy install madudka.nginx
```

Requirements
------------
Min ansible version: 2.16.8

The Ansible role should include the `become: true` parameter to ensure that tasks are executed with elevated privileges.
You can use any method to pass the `ansible_become_user` and `ansible_become_password` parameters.
More: https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_privilege_escalation.html

When using early versions of Ansible you need to install `community.general` collection:

```
ansible-galaxy collection install community.general
```


Role Variables
--------------
Default lower priority variables for this role `/defaults/main.yml`:

| Name                 | Description                            | Value example           |
|----------------------|----------------------------------------|-------------------------|
| `nginx_conf_path`    | The path to the nginx.conf file.       | /etc/nginx/nginx.conf   |
| `nginx_modules_path` | The path to the Nginx modules catalog. | /usr/lib/nginx/modules/ |

Variables associated with this role `/vars/main.yml`:

| Name                 | Description                                                   | Value example                           |
|----------------------|---------------------------------------------------------------|-----------------------------------------|
| `listen_port`        | The port that the server listens on.                          | 6443                                    |
| `servers_group_name` | The name of the server group that connections are proxied to. | k3s_servers                             |
| `server_list`        | The list of servers that connections are proxied to.          | - { ip: "192.168.0.101", port: "6443" } |

Dependencies
------------

No dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: madudka.nginx }
      become: true

License
-------

GPL-3.0-only

Author Information
------------------

https://madudka.github.io/