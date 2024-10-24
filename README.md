## Ansible 
apt-get install -y ansible
apt-get install sshpass -y
export ANSIBLE_HOST_KEY_CHECKING=False

#install cassandra
ansible-playbook main.yaml -i host -t hostname-cass
ansible-playbook main.yaml -i host -t cassandra-cluster
ansible-playbook main.yaml -i host -t cassandra-reaper

#adduser linux
ansible-playbook main.yaml -i host -t adduser

#install postgres percona
ansible-playbook main.yaml -i host -t hostname-pg
ansible-playbook main.yaml -i host -t postgres-percona-v16



