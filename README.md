# Ansible

## Install packages

Install the required packages before running `ansible-playbook`:

```bash
apt-get install -y ansible
apt-get install sshpass -y
export ANSIBLE_HOST_KEY_CHECKING=False
```

## Install Cassandra

```bash
ansible-playbook main.yaml -i host -t hostname-cass --limit worker-cassandra
ansible-playbook main.yaml -i host -t cassandra-cluster --limit worker-cassandra
ansible-playbook main.yaml -i host -t cassandra-reaper --limit host-reaper
```

## Add Linux user

```bash
ansible-playbook main.yaml -i host -t adduser --limit worker-adduser
```

<<<<<<< Updated upstream
##install postgres percona
ansible-playbook main.yaml -i host -t hostname-pg --limit worker-postgres-percona --ask-become-pass
ansible-playbook main.yaml -i host -t postgres-percona-v16 --limit worker-postgres-percona --ask-become-pass
=======
## Install Percona PostgreSQL

```bash
ansible-playbook main.yaml -i host -t hostname-pg --limit worker-postgres-percona
ansible-playbook main.yaml -i host -t postgres-percona-v16 --limit worker-postgres-percona
```
>>>>>>> Stashed changes

## Install postgres_exporter

By default, `postgres_exporter_version` is `0.20.1`. Override it with `-e` when needed.

```bash
ansible-playbook main.yaml -i host -t postgres-exporter --limit host-postgres-exporter
# Example: install a specific postgres_exporter version.
ansible-playbook main.yaml -i host -t postgres-exporter --limit host-postgres-exporter -e postgres_exporter_version=0.20.1
```

## Install MongoDB service

```bash
ansible-playbook main.yaml -i host -t mongodb --limit host-mongodb-service
```

## Install MongoDB exporter

```bash
ansible-playbook main.yaml -i host -t mongodb-exporter --limit host-mongodb-service
```

<<<<<<< Updated upstream
##install mysql-cluster
ansible-playbook main.yaml -i host -t mysql --limit mysql
=======
## Install MySQL cluster

```bash
ansible-playbook main.yaml -i host -t mysql --limit mysql
```
>>>>>>> Stashed changes
