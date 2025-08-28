# Ansible 
##install all packages before running ansible-playbook
apt-get install -y ansible
apt-get install sshpass -y
export ANSIBLE_HOST_KEY_CHECKING=False

##install cassandra
ansible-playbook main.yaml -i host -t hostname-cass --limit worker-cassandra
ansible-playbook main.yaml -i host -t cassandra-cluster --limit worker-cassandra
ansible-playbook main.yaml -i host -t cassandra-reaper --limit host-reaper

##adduser linux
ansible-playbook main.yaml -i host -t adduser --limit worker-adduser

##install postgres percona
ansible-playbook main.yaml -i host -t hostname-pg --limit worker-postgres-percona
ansible-playbook main.yaml -i host -t postgres-percona-v16 --limit worker-postgres-percona

##install postgres-exporter
ansible-playbook main.yaml -i host -t postgres-exporter --limit host-postgres-exporter

##install mongodb-service 
ansible-playbook main.yaml -i host -t mongodb --limit host-mongodb-service

##install mongodb-exporter
ansible-playbook main.yaml -i host -t mongodb-exporter --limit host-mongodb-service

##install mysql-cluster
ansible-playbook main.yaml -i host -t mysql --limit mysql