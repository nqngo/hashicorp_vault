SoftHSMv2
=========

This role install SoftHSMv2 to emulate a HSM for Vault autounseal.

Role Variables
--------------
| Name                        | Type     | Default              | Description                                      |
| --------------------------- | -------- | -------------------- | ------------------------------------------------ |
| `vault_hsm_user`            | `String` | `root`               | The user that will be using the softhsm          |
| `vault_hsm_group`           | `String` | `group`              | The group that will be using the softhsm         |
| `vault_hsm_pin`             | `String` | `1234`               | The SoftHSM user pin                             |
| `vault_hsm_so_pin`          | `String` | `1234`               | The SoftHSM SO pin                               |
| `vault_hsm_token_label`     | `String` | `vault-hsm-key`      | The SoftHSM Slot Token Label                     |
| `vault_hsm_package`         | `String` | `softhsm`            | SoftHSM package name                             |
| `vault_softhsm_log_level`   | `String` | `ERROR`              | Log level: `ERROR`, `WARNING`, `INFO` or `DEBUG` |
| `vault_softhsm_config_path` | `String` | `/etc/softhsm2.conf` | The default config path                          |
| `vault_softhsm_token_dir`   | `String` | `/opt/vault/hsm`     | The directory where the token is stored          |

Dependencies
------------

NONE

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - role: nqngo.hashicorp_vault.vault_softhsm
```

License
-------

GPL-2.0-or-later

Author Information
------------------

Nhat Ngo
