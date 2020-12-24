# Role Names

kubernetes-cluster-init

This roles is only for master and node initizalization only. It work only in CentOS 8

## Configuration

Below are the example to run this ansible role:

playbook.yml

  ```  
    - name: Kubernetes Initialization
      hosts: kube-node #including master node
      roles:
        - role: kubernetes-cluster-init
          user: kubeadmin # default user is kubeadmin
```

ansible.cfg:

  ```  
    [defaults]
    remote_user=sysadmin
    host_key_checking=false
    inventory=inventory

    [privilege_escalation]
    become=true
    become_method=sudo
    become_user=root
    become_ask_pass=false
  ```

inventory:

  ```  
    [master-node]
    master

    [worker-node]
    worker1
    worker2

    [kube-node:children]
    master-node
    worker-node
  ```

## Author Information

MK (Meor Muhammad Kamil).
