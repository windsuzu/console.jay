---
draft: false
date: 2024-05-16 11:48
tags:
  - postgres
---

Install Postgres on WSL 2 (Ubuntu):

```bash
sudo apt update
sudo apt install postgresql
psql --version
```

If the version of Postgres that corresponds to your Ubuntu is not what you want, you can use the [PostgreSQL Apt Repository](https://apt.postgresql.org/). It will provide automatic updates for all supported versions of Postgres.

```bash
# Automated repository configuration
sudo apt install -y postgresql-common
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh

# Install again
sudo apt install postgresql
psql --version
```


> [!info] References
> - [PostgreSQL: Linux downloads (Ubuntu)](https://www.postgresql.org/download/linux/ubuntu/)
> - [Install and use Postgres in WSL - DEV Community](https://dev.to/sfpear/install-and-use-postgres-in-wsl-423d)
