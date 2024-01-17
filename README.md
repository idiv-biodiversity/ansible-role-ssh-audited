Ansible Role: OpenSSH
=====================

An Ansible role that configures OpenSSH based on the latest [ssh-audit][]
recommendations.

Table of Contents
-----------------

<!-- toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
  * [Top-Level Playbook](#top-level-playbook)
  * [Role Dependency](#role-dependency)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

Requirements
------------

- Ansible 2.9

Role Variables
--------------

This role only **sets** variables from [idiv_biodiversity.ssh][].

**Note:** The hardened defaults that this role sets may be different based on
the targeted platform/OS/distro due to what its version of OpenSSH supports.

Dependencies
------------

```yml
---

# requirements.yml

roles:

  - name: idiv_biodiversity.ssh
    src: https://github.com/idiv-biodiversity/ansible-role-ssh
    version: vX.Y.Z

  - name: idiv_biodiversity.ssh_audited
    src: https://github.com/idiv-biodiversity/ansible-role-ssh-audited
    version: vX.Y.Z

...
```

Example Playbook
----------------

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: servers
  hosts: servers

  roles:

    - role: idiv_biodiversity.ssh_audited
      tags:
        - ssh

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv_biodiversity.ssh_audited
    tags:
      - ssh

...
```

License
-------

MIT

Author Information
------------------

This role was created in 2020 by [Christian Krause][author] aka [wookietreiber
at GitHub][wookietreiber], HPC cluster systems administrator at the [German
Centre for Integrative Biodiversity Research (iDiv)][idiv].

[author]: https://www.idiv.de/en/groups_and_people/employees/details/61.html
[idiv]: https://www.idiv.de/
[idiv_biodiversity.ssh]: https://galaxy.ansible.com/idiv_biodiversity/ssh
[ssh-audit]: https://github.com/jtesta/ssh-audit
[wookietreiber]: https://github.com/wookietreiber
