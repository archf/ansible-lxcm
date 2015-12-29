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
lxc_pkg_state: installed
```

vars/Debian.yml:

```yaml
lxc_packages:
  - lxc
  - lxc-templates
  - python3-lxc
```

vars/RedHat.yml:

```yaml
lxc_packages:
  - lxc
  - lxc-extra
  - lxc-templates
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

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
