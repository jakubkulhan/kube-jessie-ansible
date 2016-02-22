# Kubernetes set-up on Debian Jessie using Ansible

```sh
$ cp inventory.example inventory
# edit inventory file
$ ansible-playbook -i inventory -e kube_master_ip=... playbook.yml
```
