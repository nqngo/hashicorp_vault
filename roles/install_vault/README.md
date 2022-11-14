Install Vault
=============

This role Vault as a Cluster using Raft backend.

Role Variables
--------------
| Name | Type | Default | Description |
|---|---|---|---|
| `vault_api_addr` | `String` | `ansible_facts['default_ipv4']['address']` | Cluster API Address, preferably set to LB |
| `vault_api_port` | `String` | `8200` | Cluster API port |
| `vault_cluster_addr` | `String` | `ansible_facts['default_ipv4']['address']` | Vault cluster address, preferably set to LB |
| `vault_cluster_name` | `String` | `vault-production` | The cluster name |
| `vault_cluster_port` | `String` | `8201` | Vault Cluster port |
| `vault_config_path` | `String` | `/etc/vault.d/vault.hcl` | Path to vault config file |
| `vault_lic_src_path` | `String` | `/opt/vault.lic` | Vault Enterprise license path on computer running the playbook |
| `vault_lic_dest_path` | `String` | `/etc/vault.d/license.hclic` | Where to copy the license file to in Vault servers |
| `vault_raft_members` | `Hashmap[]` | Current inventory node | The members of Raft cluster. See FAQS below |
| `vault_raft_path` | `String` |  `/opt/vault/data` | The Raft filestore path |
| `vault_raft_performance_multiplier` | `Integer` | 1 | The Raft performance multiplier tuning |
| `vault_systemd_path` | `String` | `/etc/systemd/system/vault.service` | The path to put the systemd service |
| `vault_tls_disable` | `Bool` | `true` | Disable Vault TLS |
| `vault_use_hashicorp_repo` | `Bool` | `true` | Setup Hashicorp repository |
| `vault_version` | `String` | `vault-1.12.1-1` | The Vault version to install |

Dependencies
------------

NONE

Example Playbook
----------------

```yaml
    - hosts: servers
      vars:
        vault_raft_members:
          - ip: "{{ hostvars['redhat8-vault-1']['ansible_default_ipv4']['address'] }}"
            port: 8200
          - ip: "{{ hostvars['redhat8-vault-2']['ansible_default_ipv4']['address'] }}"
            port: 8200
          - ip: "{{ hostvars['redhat8-vault-3']['ansible_default_ipv4']['address'] }}"
            port: 8200
      roles:
         - role: nqngo.hashicorp_vault.install_vault
```

FAQS
----
1. Why set `vault_raft_members` as a `var` instead of inferring from the inventory?
  > This is will allow us to ensure we do not accidentally remove the Raft members from
    the Vault config when running with the `--limit` flag.

License
-------

GPL-2.0-or-later

Author Information
------------------

Nhat Ngo
