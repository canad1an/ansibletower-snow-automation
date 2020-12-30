# Avi Networks ServiceNow Automation with Ansible

This script is part of a larger automation workflow. The flow is ServiceNow Catalog Form -> Ansible Tower -> Ansible -> Avi Controller

## Variables
/vars/creds.yaml - Login credentials for the Avi Controller

```
avi_controller_username: myusername
avi_controller_password: mypassword1!
```

Example extra variables:
```
ApplicationName: test-application-80
ApplicationType: http
Department: Sales
Environment: aws
HealthMonitor: ping
ListeningPort: '80'
PoolMembers: '10.1.1.1,80,enabled::10.2.2.2,8080,enabled'
```

## Usage
It is recommended that you always use an encrypted vault. The creds.yaml file needs to be encrypted.

Run the playbook with vault password and extra vars:
```
ansible-playbook single_site_virtual_create.yaml --ask-vault-pass --extra-vars "ApplicationName: test-application-80 ApplicationType: http Department: Sales HealthMonitor: ping ListeningPort: '80'PoolMembers: '10.1.1.1,80,enabled::10.2.2.2,8080,enabled'"
```

Run the playbook without vault:
```
ansible-playbook single_site_virtual_create.yaml
```

Run the playbook with vault password file:
```
ansible-playbook single_site_virtual_create.yaml --vault-password-file ../vault_pass
```

Run the playbook with vault password:
```
ansible-playbook single_site_virtual_create.yaml --ask-vault-pass
```