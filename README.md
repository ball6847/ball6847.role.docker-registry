Ansible Role - ball6847.role.docker-registry
============================================

Setup docker registry via docker and docker-compose

Requirements
------------

- docker
- docker-compose

Role Variables
--------------

**docker_registry_path**: `/opt/docker/registry`

Path to place docker-compose.yml file into.

**docker_registry_volume**: `/var/lib/registry`

Path on host to store registry data.

**docker_registry_port**: `5000`

Port to run registry on.

**docker_registry_config_file**: `files/config.yml`

Path to `config.yml` of registry, this role comes with handy `config.yml`, if you need to configure these values yourself,
make sure you override this variable and point it to your real `config.yml` file.

Please note that you should always prepend your value with `{{ playbook_dir }}` to make it completely ignore files in role.

**docker_registry_compose_file**: `templates/docker-compose.yml.j2`

Path to docker-compose.yml template file, to use your version of this file, please read instruction above (`docker_registry_config_file`) on how to this correctly.


Dependencies
------------

none

Example Playbook
----------------

```yml
- name: Docker Registry
  hosts: all
  become: yes
  tags: [ registry ]
  roles:
    - { role: ball6847.role.docker-registry }
```

To override default template file.

```yml
- name: Docker Registry
  hosts: all
  become: yes
  tags: [ registry ]
  roles:
    - { role: ball6847.role.docker-registry, docker_registry_compose_file: "{{ playbook_dir }}/templates/docker-compose.yml.j2" }
```

License
-------

BSD

Author Information
------------------

Porawit Poboonma

Credits
------

- [Registry](https://hub.docker.com/_/registry/) - Docker image used by this role.
