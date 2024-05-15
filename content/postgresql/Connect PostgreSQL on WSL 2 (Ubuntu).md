---
draft: false
date: 2024-05-15 16:36
tags:
  - postgres
---

To connect to Postgres, you first need to give the default Postgres admin user `postgres` a password using `sudo passwd postgres`. Then run the `psql` command with the `postgres` identity using `sudo -u postgres`.

```bash
sudo passwd postgres
sudo -u postgres psql
```

### Create a user

If you don't want to use the default `postgres` admin user. You can create your own admin user by following the steps below.

```bash
sudo -u postgres createuser --interactive
# Enter name of role to add: windsuzu
# Shall the new role be a superuser? (y/n) y
```

Then edit `pg_hba.conf`, which is located in `/etc/postgresql/<version>/main`.

```bash
sudo vim /etc/postgresql/16/main/pg_hba.conf
```

Scroll to the bottom of the file and change all the `peer` to `trust`.

```conf
local   all             postgres                                trust
local   all             all                                     trust
```


> [!info] References
> - [Install and use Postgres in WSL - DEV Community](https://dev.to/sfpear/install-and-use-postgres-in-wsl-423d)
