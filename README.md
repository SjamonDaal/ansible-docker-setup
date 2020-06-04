<p align="center"><a href="https://www.sdhd.nl/link.php?id=32" alt="Secure & Reliable Hosting"><img src="https://www.sdhd.nl/assets/img/logo.png" width="245px;"></a></p>

## Ansible - Docker Setup
This Ansible playbook install docker and docker-compose with the latest version of docker.

## Documentation

#### Ansible tags list

- docker
 - Just installs docker and skips other tags.
- docker-compose
 - Just installs docker-compose and skips other tags.

#### Example for the hosts.yml file
Example with DNS hostnames and the same SSH username as your system
```YAML
all:
  hosts:
    hostname-01:
    hostname-02:
```

Example with another username and no dns server that could resolve the hostnames.
```YAML
all:
  hosts:
    hostname-01:
      ansible_user: ubuntu
      ansible_host: 192.168.1.10
    hostname-02:
      ansible_user: ubuntu
      ansible_host: 192.168.1.11
```

#### Example for the variables.yml file
```YAML
---

- name: Set facts for environment
  set_fact:
    custom_user:
      available: true
      username: ubuntu
    docker:
      # Docker versions: stable, nightly, test
      version: stable
    docker_compose:
      version: "1.26.0"
```

#### Example ansible commands
Default example to run the playbook
```bash
ansible-playbook -i hosts.yml site.yml -vvvv
```

Custom example with specific tags
```bash
ansible-playbook -i hosts.yml site.yml --tags=docker,docker-compose -vvvv
```

Custom example with hostname limit
```bash
ansible-playbook -i hosts.yml site.yml --limit=hostname-01 -vvvv
```


## Credits
Build and Managed by: Djamon Staal
