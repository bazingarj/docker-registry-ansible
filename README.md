# Docker Registry Ansible Playbook

This Ansible playbook automates the installation and configuration of a private Docker Registry on Ubuntu (Debian) and RedHat-based systems.

## Usage

1. **Clone the repository:**
```sh
git clone <repo-url>
cd docker-registry-ansible
```

2. **Define your inventory:**
Create an inventory.ini file with your target hosts:
```
[docker_registry]
your.server.address
```

3. **Set variables (optional):**
You can override default variables by creating a group_vars/docker_registry.yml or passing them with -e.

Example group_vars/docker_registry.yml:
```
user: docker
group: docker
registry_path: /opt/docker-registry
registry_data: /opt/docker-registry/data
```

4. **Run the playbook:**
```
ansible-playbook -i inventory.ini playbook.yml
```

**What it does:**
* Installs Docker and Docker Compose
* Creates a dedicated user and group
* Sets up required directories
* Deploys a Docker Compose file for the registry
* Starts the Docker Registry container
* Verifies the registry is running on port 5000

**OS Support:**
* Ubuntu (Debian family)
* RedHat/CentOS

**Notes:**
* Ensure your user has sudo privileges on the target machine.
* The playbook uses variables for flexibility; adjust them as needed.
* The Docker Compose template should be placed in roles/docker-registry/tasks/templates/docker-compose.yaml.j2
