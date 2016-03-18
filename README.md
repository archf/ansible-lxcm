ansible-lxcm
============

An ansible role to manage lxc container instances on a host. The goal is to get vagrant, vagrant-lxc, livirt-lxc out of the way.

Requirements
------------

Add folling line to your inventory file (/etc/ansible/hosts):

```yaml
localhost ansible_ssh_host=localhost ansible_connection=local
```

None.

Role Variables
--------------

defaults/main.yml:

```yaml
lxcm_default_grp: "{{ ansible_hostname }}_c"
lxcm_child_grp:
  - "all_c"
lxcm_domain: "lxc"

Dependencies
------------

It requires a working lxc installation.

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - { role: archf.lxc }
```
Define useful alias

```bash
# start container (akin to vagrant up)
alias acu="ansible -i local -e lxcm_state=started"

# start container (akin to vagrant halt)
alias ach="ansible -i local -e lxcm_state=stopped"

# start container (akin to vagrant reload)
alias acu="ansible -i local -e lxcm_state=restarted"

# start container (akin to vagrant destroy)
alias acd="ansible -i local -e lxcm_state=absent"

# freeze container
alias acu="ansible -i local -e lxcm_state=frozen"
```

License
-------

MIT

Author Information
------------------

Felix Archambault
