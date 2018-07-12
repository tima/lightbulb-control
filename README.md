lightbulb-control
=========

Sets up a Red Hat Enterprise Linux 7 or CentOS 7 base node for use as the controller in an Ansible Lightbulb lab environment.

This role will:

* Ensures the EPEL repository has been enabled
* Ensures the latest version of useful command line tools are present
    * vim
    * git
    * wget
    * nano
    * sshpass
* (Optionally) Ensures the latest version of Ansible is present
* Ensures a clone of the ansible/lightbulb content is in user home
* Configures ansible and vim

Requirements
------------

Fact gathering should have been run on the host.

Role Variables
--------------

* *username*: This *required* variable contains a string with the student username that will be using the node in their lab. This variable is typically elsewhere using `set_fact` while provisioning or as a host variable in more static environments.

* *control_node_inventory_path*: This variable is defines the absolute path of the lab's static inventory file. The default is `/home/{{ username }}/inventory.ini`.

* *control_node_install_ansible*: A boolean value that controls if the role should pre-install install ansible. The variable defaults to "false".

Dependencies
------------

The lightbulb-common-linux role (or similar tasks) should have been executed to prepare the node.

Example Playbook
----------------

```yaml
---
- hosts: control
  vars:
    username: lightbulb
  roles:
    - lightbulb-control
```

License
-------

MIT

Author Information
------------------

This role has been developed as part of the [Ansible Lightbulb project](https://github.com/ansible/lightbulb).
