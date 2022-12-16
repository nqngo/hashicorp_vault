Autounseal Vault with HSM
=============

This role configure Vault with HSM Autounseal. It requires a functioning Vault cluster.

Role Variables
--------------
| Name                              | Type     | Default                          | Description               |
| --------------------------------- | -------- | -------------------------------- | ------------------------- |
| `vault_autounseal_hmac_key_label` | `String` | `vault-hsm-hmac-key`             | HSM HMAC key label        |
| `vault_autounseal_hsm_key_label`  | `String` | `vault-hsm-key`                  | HSM Key Label             |
| `vault_autounseal_hsm_slot`       | `String` | `0`                              | The HSM Slot              |
| `vault_autounseal_hsm_pin`        | `String` | `1234`                           | HSM Pin                   |
| `vault_autounseal_lib_path`       | `String` | `/lib64/softhsm/libsofthsm.so`   | The lib path to HSM       |
| `vault_config_path`               | `String` | `/etc/vault.d/vault-cluster.hcl` | Path to Vault config file |
| `vault_hsm_token_label`           | `String` | `vault-hsm-token`                | Vault HSM Token Name      |


Dependencies
------------

NONE

Example Playbook
----------------

```yaml
    - hosts: servers
      vars:
        vault_autounseal_hmac_key_label: vault-hsm-hmac-key
        vault_autounseal_hsm_key_label: vault-hsm-key
        vault_autounseal_hsm_slot: "0"
        vault_autounseal_hsm_pin: "1234"
        vault_autounseal_lib_path: "/lib64/softhsm/libsofthsm.so"
      roles:
         - role: nqngo.hashicorp_vault.autounseal_vault_hsm
```

License
-------

GPL-2.0-or-later

Author Information
------------------

Nhat Ngo
