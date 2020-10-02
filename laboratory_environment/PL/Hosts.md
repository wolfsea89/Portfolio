Utworzenie inventory - hosts
=========

Inventory jest to konfiguracjia dostarczana do playbooków. Tutaj powinny znaleźć się wszystkie parametry konfgiracyjne. Dobrą praktyką jest to, aby w playbookach i rolach nie było parametrów konfiguracyjnych, a jedynie defaultowe.

Struktura inventory
=========
```
.
├── group_vars
│   (...)
├── host_vars
│   ├── mr-reactor-002
│   ├── mr-router-001
│   ├── mr-vm-021
│   ├── mr-vm-022
│   ├── mr-vm-023
│   ├── mr-vm-024
│   └── mr-vm-025
├── prod-servers
└── test-serves
```

Iventory Hosts
=========
Utworzenie mapy przynaleźności hostów do grup w inventory:

test-servers
```
all:
  children:
    routeros:
      hosts:
        mr-router-001:
    virtual_machine:
      children:
        test:
          hosts:
            mr-vm-021:
            mr-vm-022:
            mr-vm-023:
            mr-vm-024:
            mr-vm-025:
    docker:
      children:
        test:
          hosts:
            mr-vm-021:
            mr-vm-022:
            mr-vm-023:
            mr-vm-024:
            mr-vm-025:
```
prod-servers
```
all:
  children:
    routeros:
      hosts:
        mr-router-001:
    virtual_machine:
      children:
        production:
          hosts:
            mr-reactor-002:
    docker:
      children:
        production:
          hosts:
            mr-reactor-002:
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

[Ansible.Inventory.Example](https://github.com/wolfsea89/Ansible.Inventory.Example.git)

[Powrót](../../README.md)