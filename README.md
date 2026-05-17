# Homeserver
System configuration for my personal Debian homeserver.

## Infrastructure as Code

**Ansible** is used to configure the system. 

### Current Secret Management: Local Environment Variables
Until Ansible Vault is introduced to this project, sensitive infrastructure data is stored in a local environment file. Ansible accesses this data via the `lookup` plugin.

#### Setup Instructions:
1. Create a `.env` file in the root directory of this project:
   ```text
   export SERVER_IP="your_ip"
   export ANSIBLE_USER="your_username"
   export ANSIBLE_PORT="your_port"
   ```
2. Load the environment variables and run the playbook:
    ```bash
    source ../.env && ansible-playbook -i inventory.ini playbook.yml
    ```