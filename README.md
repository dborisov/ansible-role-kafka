# ansible-role-kafka

Ansible role to install Apache Kafka

## Supported Platforms

- RedHat 7
- RedHat 8

## Requirements

- The role supports the installation of Kafka version 2.1.0 and higher. Default is 3.0.0
- Java must be installed on the server before using this role. You can use your own java role or see an example of installing Java in tests in the prepare.yml file
- The Zookeeper cluster must be installed on separate servers. This role also supports the built-in Zookeeper (see `molecule/default/converge.yml`), but this configuration is not recommended for production use. Please use it for development and testing purposes only.

## Example Inventory

```
[zookeeper_cluster]
zk1.local zookeeper_id=1
zk2.local zookeeper_id=2
zk3.local zookeeper_id=3

[kafka_cluster]
kafka1.local kafka_broker_id=1
kafka2.local kafka_broker_id=2
kafka3.local kafka_broker_id=3
```

## Example Playbook

```
---
- hosts: zookeeper_cluster
  roles:
    - role: dborisov.java
    - role: dborisov.zookeeper

- hosts: kafka_cluster
  roles:
    - role: dborisov.java
    - role: dborisov.kafka
```

## Role Variables

Please see `defaults/main.yml`

## Dependencies

None

## License

MIT
