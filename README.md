## Ansible 
apt-get install -y ansible
apt-get install sshpass -y
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook main.yaml -i host -t cassandra-cluster
ansible-playbook main.yaml -i host -t cassandra-reaper
ansible-playbook main.yaml -i host -t adduser
ansible-playbook main.yaml -i host -t postgres-percona-v16
##status handlers
reloaded, restarted, started, stopped


#login cass
cqlsh -u cassandra  -p cassandra