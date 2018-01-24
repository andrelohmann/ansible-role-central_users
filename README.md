central_users
=============

[![Build Status](https://travis-ci.org/andrelohmann/ansible-role-central_users.svg?branch=master)](https://travis-ci.org/andrelohmann/ansible-role-central_users)

Deploy users and public keys to your machines. This role allows to manage a central users library and setting subsets of users for each machine.

Role Variables
--------------

Create a central list with all users you are going to spread over all available machines. You can set every parameter for the user that is available from http://docs.ansible.com/ansible/user_module.html. Also you can set every parameter (exept "user" and "append" which defaults to 'no') for the key that is available from http://docs.ansible.com/ansible/authorized_key_module.html. You can put the central users directly into the playbook, the host/group vars or into a centrally managed vars file.

    central_users_var_file: __PATH_TO_YOUR_CENTRAL_USERS_VARIABLE__
    central_users:
      __USERNAME__:
        uid: __UID__
        state: present
        public_keys:
        - key: ssh-rsa AAA...
          state: present

For each host/group, create a separate machine_users dictionary, listing all users that need to be deployed (or removed) from the desired machines. YOu can set the state and a list of groups.

    machine_users:
      __USERNAME__:
        sudo: true
        state: 'present'
        groups:
        - group1
        - group2

Example Playbook
----------------

    - hosts: central_users
      roles:
         - { role: andrelohmann.central_users }

License
-------

MIT

Author Information
------------------

https://github.com/andrelohmann
