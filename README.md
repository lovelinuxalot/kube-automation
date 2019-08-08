Kubernetes Cluster Automation with Vagrant and Ansible:

Steps to follow:

- Run vagrant up to spin up the instances
- Run the master playbook to setup master node
- Run the node-playbook to setup worker nodes

For existing Vagrant boxes:

- Run Vagrant up to spin up the boxes
- run the master playbook with "start_ks" tag ```ansible-playbook master-playbook.yml --tags "start_ks"```

