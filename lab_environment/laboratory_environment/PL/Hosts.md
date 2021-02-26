Utworzenie inventory - hosts
=========

Inventory jest to to przestrzeń na konfigurację, która jest dostarczana do playbooków. Tutaj powinny znaleźć się wszystkie parametry konfiguracyjne. Dobrą praktyką jest to, aby w playbookach i rolach nie było parametrów konfiguracyjnych, a jedynie domyślne.

Struktura inventory
=========
```
.
├── group_vars
│   (...)
├── host_vars
|   ├── mr-rou-001.rachuna.net:
│   ├── localhost.yml
│   ├── jenkins-master.rachuna.net
│   ├── jenkins-slave.rachuna.net
└── hosts
```

Iventory Hosts
=========
Utworzenie mapy przynależności hostów do grup w inventory:

```
all:
  children:
    workstasion:
      hosts:
        localhost:
    jenkins:
      children:
        jenkins_master:
          hosts:
            jenkins-master.rachuna.net:
        jenkins_slave_linux:
          hosts:
            jenkins-slave.rachuna.net:
```

Tworzenie host_vars
=========

(!) Możliwe jest podzielenie inventory w host_vars na pojedyńcze pliki (np. main.yml, packages.yml) itd.

host_vars/<< hostname >>/main.yml
```
ansible_host: 10.1.0.23

system:
  os_distribution: "Ubuntu"
  os_version: "20.04"
```

Przykładowe inventory
=========

[Ansible-Inventory-Example](https://github.com/wolfsea89/Ansible-Inventory-Example.git)

[Powrót](../../../README.md)