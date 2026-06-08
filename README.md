# My Homeserver

This repository contains the Infrastructure as Code (IaC) configuration for my personal homeserver, managed using Ansible.

<details>
<summary> Compatibility Notice </summary>

> This project is tested only on Debian. It relies on apt for package management and systemd for service orchestration.
>
> If you intend to use this configuration on a different operating system, please be aware that refactoring of the roles and tasks will be required.
</details>

## Getting Started

Prerequisites:
 - A control node with Ansible.
 - A target host with SSH access and sudo privileges.

## Deployment
1. Create a `.env` file in the root directory of this project:
   ```text
   export SERVER_IP="your_ip"
   export ANSIBLE_USER="your_username"
   export ANSIBLE_PORT="your_port"
   export PIHOLE_PASSWORD="your_pihole_password"
   export PAPERLESS_DB_PASSWORD="your_paperless_db_password"
   ```
2. Load the environment variables and run the playbook:
    ```bash
    source ../.env && ansible-playbook playbook.yml --ask-become-pass
    ```

## TODO

- [ ] Simplify directory creation in all ansible tasks

## FAQ

<details>
<summary><strong>Why use a .env file?</strong></summary>

> Committing credentials or other sensitive values to a public repository is never a good idea. The .env file allows quick edits during active active development. Once the project’s features and services are more stable, the plan is to transition to Ansible Vault.
</details>

<details>
<summary><strong>Why am I seeing SSL/TLS certificate warnings?</strong></summary>

> This setup uses Caddy’s self‑signed certificates, your device won’t trust them automatically. To fix this, you must import the local root certificate into your system’s trust store.
>
> Root certificate location:
> `/srv/caddy/data/caddy/pki/authorities/local/root.crt`
</details>

