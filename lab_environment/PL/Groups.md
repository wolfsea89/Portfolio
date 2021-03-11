Utworzenie inventory - gropus
=========

Inventory jest to to przestrzeń na konfigurację, która jest dostarczana do playbooków. Tutaj powinny znaleźć się wszystkie parametry konfiguracyjne. Dobrą praktyką jest to, aby w playbookach i rolach nie było parametrów konfiguracyjnych, a jedynie domyślne.

Struktura inventory
=========
```
.
├── group_vars
│   ├── all
│   ├── jenkins
│   ├── jenkins_master
│   ├── jenkins_slave_linux
│   ├── routeros
│   └── workstasion
├── host_vars
│   (...)
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

Tworzenie group_vars
=========

(!) Możliwe jest podzielenie inventory w group_vars na pojedyńcze pliki (np. main.yml, packages.yml) itd.

group_vars/<< groupname >>/users.yml
```
all:
  users:
    - name: Maciej Rachuna
      username: maciej-rachuna
      default_password: "aaaa"
      state: present
      public_keys: 
        - 'ssh-rsa AAAA'

    - name: Test User
      username: test-user
      default_password: "aaa"
      state: present
      public_keys: 
        - 'ssh-rsa AAAA'
```

Przykładowe inventory
=========

[Ansible-Inventory-Example](https://github.com/wolfsea89/Ansible-Inventory-Example.git)

[Powrót](../../../README.md)
