SoftHSMv2
=========

This role install SoftHSMv2 to emulate a HSM for Vault autounseal.

Role Variables
--------------
| Name | Type | Default | Description |
|---|---|---|---|
| `vault_hsm_pin` | `String` | `1234` | The SoftHSM user pin |
| `vault_hsm_so_pin` | `String` | `1234` | The SoftHSM SO pin |
| `vault_hsm_token_label` | `String` | `1234` | The SoftHSM Slot Token Label |

Dependencies
------------

NONE

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - role: nqngo.hashicorp_vault.softhsm
```

License
-------

GPL-2.0-or-later

Author Information
------------------

Nhat Ngo
