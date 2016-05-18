1. create.yaml - will create the jump box, the app server and the AWS security group to restrict SSH access

2. configureapp.yaml - Configures the app server per your spec. EPEL repo and NTP are installed, stratum is checked, OpenLDAP server installed and started, security group created and sudoers/access files modified. This would need to be run from the jump box that has the SSH keys. I have been using this command to execute it with my key:

ansible-playbook configureapp.yaml -u ec2-user -i app_inventory --private-key=justin.pem --become 

3. check.yaml - does a health check on the app server. Reports Slapd status, port 389 status and system load. should also be called with SSH keys