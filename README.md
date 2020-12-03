# Deploying Cassandra cluster in Vagrant using Ansible

## Required tools set:
- LibVirt
- Vagrant

## Execution steps:
- Install libvirt and vagrant
- git clone https://github.com/simon3270/vagrant-cassandra.git
- cd vagrant-cassandra
- vagrant up

## Output:
Vagrant will start a controller node and three Cassandra nodes runnig CentOS 7, and an Ansible playbook will execute a set of tasks. Eventually a Cassandra cluster status will be displayed.

## Directory structure
``` sh
ansible.cfg - manage Ansible configuration on the controller node
CassandraCluster.yml - the Ansible playbook to install Cassandra
inventory.yml - describes the nodes for Ansible
Vagrantfile - describes the nodes for Vagrant
└── roles - the Ansible role(s) to be used
    └── cassandra-cluster
        ├── handlers
        │   └── main.yml - perform post-install checks
        ├── tasks
        │   └── main.yml - perform the installation
        ├── templates
        │   ├── cassandra.service.j2 - the systemd unit file
        │   └── cassandra.yaml.j2    - the Cassandra configuration
        └── vars
            └── main.yml - variables describing Cassandra
```

