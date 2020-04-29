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

None.

Role Variables
--------------

This role only **sets** variables from [idiv-biodiversity.ssh][].

Dependencies
------------

This role depends on [idiv-biodiversity.ssh][].

Example Playbook
----------------

Add to `requirements.yml`:

```yml
---

- src: idiv-biodiversity.ssh-audited

...
```

Download:

```console
$ ansible-galaxy install -r requirements.yml
```

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: head server
  hosts: heads

  roles:
    - role: idiv-biodiversity.ssh-audited
      tags:
        - ssh

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv-biodiversity.ssh-audited
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

[author]: https://www.idiv.de/groups_and_people/employees/details/eshow/krause-christian.html
[idiv]: https://www.idiv.de/
[idiv-biodiversity.ssh]: https://galaxy.ansible.com/idiv-biodiversity/ssh
[ssh-audit]: https://github.com/jtesta/ssh-audit
[wookietreiber]: https://github.com/wookietreiber
