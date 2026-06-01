# pg-database

An Ansible role to create a PostgreSQL database and user.

It can be executed on any node, not especially the one where the application using the DB will be used, as the role connects to the cluster to create the database and user.

## Requirements

Requires the `community.postgresql` Ansible collection.

## Role Variables

- `cluster_host`: PostgreSQL cluster host
- `cluster_admin_user`: PostgreSQL cluster admin user
- `cluster_admin_password`: PostgreSQL cluster admin password
- `app_db_user`: Application database user
- `app_db_password`: Application database password
- `app_db_name`: Application database name

## Dependencies

Relies on `geerlingguy.pip` to install the required Python library.

## Example Playbook

```yaml
---
- name: Tests
  hosts: tests
  roles:
    - role: bastantoine.pg-database
      vars:
        cluster_host: db.example.com
        cluster_admin_user: "admin"
        cluster_admin_password: "{{ admin_password }}"
        app_db_name: "db"
        app_db_user: "user"
        app_db_password: "{{ user_password }}"
```

## License

MIT
