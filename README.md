# Kubernetes set-up on Debian Jessie using Ansible

```sh
$ cp inventory.example inventory
# edit inventory file
$ ansible-playbook -i inventory -e 'kube_master_ip=... kubelet_bind_interface=eth0' playbook.yml
```
