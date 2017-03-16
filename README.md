# Kubernetes set-up on Debian Jessie using Ansible

- For small Kubernetes clusters (< 20 nodes).
- Kubernetes version see `kube_release` variable in `playbook.yml`.
- No dedicated master node - `apiserver`, `controller-manager` and `scheduler` are just another Kubernetes pod local to specified master instance.
- No authentication to `apiserver`.
  - Cluster is expected to be run on a private network, `apiserver` will be bound to given `kube_master_ip`, ensure using firewall that only cluster nodes can access ports `8081` and `6443` on given IP.
  - If you need to access `apiserver` from outside world, add `nginx` with basic auth in front of it.
- [Calico](http://www.projectcalico.org/) networking.
- TODO: `fluentd` (or similar) + cluster logging with Elasticsearch+Kibana.

```sh
$ cp inventory.example inventory
# edit inventory file to match your configuration
$ ansible-playbook -i inventory -e 'kube_master_ip=... kubelet_bind_interface=eth0' playbook.yml
```
