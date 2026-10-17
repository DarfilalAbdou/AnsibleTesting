Ansible project to deploy a small Docker application stack on a remote Debian host.

What it deploys
- Docker runtime and Docker SDK
- App network named app-network
- PostgreSQL container named database using darfilalabdou/tp-devops-database
- API container named simple-api using darfilalabdou/tp-devops-simple-api
- Reverse proxy container named proxy using darfilalabdou/tp-devops-httpd, exposed on port 80

Inventory
- File: inventories/setup.yml
- Target group: prod
- Host: abdou-samad.darfilal.takima.school
- SSH user: admin
- SSH key: /home/Darfilal/id_rsa

Playbooks
- setup.yml: basic connectivity test using ansible ping
- playbook.yml: full deployment of the stack
- dockerbook.yml: same deployment role flow as the main stack playbook

Roles
-app : deployment of the back-end of the website
-database: deployment of the database
-docker: installation of the docker modules
-network : deployment of the network of communication for the app. (database api and reverse-proxy)
-proxy : deployment of the reverse proxy
Run
ansible-playbook -i inventories/setup.yml setup.yml
ansible-playbook -i inventories/setup.yml playbook.yml

Requirements
- Ansible installed on the control machine
- SSH access to the target host
- Docker repository access and root/sudo privileges on the remote host

Notes
- The database is configured with PostgreSQL database db, user usr, password pwd.
- The app and proxy containers are attached to the app-network Docker network.
