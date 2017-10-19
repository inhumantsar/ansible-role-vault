# inhumantsar.vault

## What?

Stands up Hashicorp Vault as a Docker Compose based service.

*NOTE:* This is not meant for use in production.

## How?
```bash
yum clean all && yum update -y
yum install -y git gcc python-devel openssl-devel

pip install ansible

echo -e """- src: geerlingguy.docker
- src: inhumantsar.vault""" > requirements.yml

ansible-galaxy install -r requirements.yml

echo """---
- hosts: localhost
  roles:
   - geerlingguy.docker
   - inhumantsar.vault""" > playbook.yml

ansible-playbook playbook.yml
```

### Decommission
```bash
ansible-playbook playbook.yml -e service_state=absent```
