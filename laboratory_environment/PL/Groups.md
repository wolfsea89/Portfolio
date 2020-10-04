Utworzenie inventory - gropus
=========

Inventory jest to to przestrzeń na konfigurację, która jest dostarczana do playbooków. Tutaj powinny znaleźć się wszystkie parametry konfiguracyjne. Dobrą praktyką jest to, aby w playbookach i rolach nie było parametrów konfiguracyjnych, a jedynie domyślne.

Struktura inventory
=========
```
.
├── group_vars
│   └── all
│       ├── main.yml
│       └── users.yml
├── host_vars
├── prod-servers
└── test-serves
```

Iventory Hosts
=========
Utworzenie mapy przynależności hostów do grup w inventory:

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

[Ansible.Inventory.Example](https://github.com/wolfsea89/Ansible.Inventory.Example.git)

[Powrót](../../README.md)
