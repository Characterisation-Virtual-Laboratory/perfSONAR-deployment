perfSONAR Toolkit Deployment
============================

This Ansible role performs a deployment of the perfSONAR Toolkit. perfSONAR is a
collection of tools used for performing end-to-end network measurements. The toolkit
enables scheduling of regular tests and for the results to be stored in a database
for future reference.

Let's Encrypt's CertBot is used to obtain SSL certificates for Apache.

https://www.perfsonar.net/

User documenation: http://docs.perfsonar.net/

The role was developed using these instructions: http://docs.perfsonar.net/install_debian.html

For information on using Ansible: https://docs.ansible.com/ansible/latest/index.html

Requirements
------------

The role has been tested on Ubuntu 18.04.

For firewall settings please refer to: https://www.perfsonar.net/deployment_security.html#default-firewall-rules-and-requirements

A DNS entry is required before installing this role.

Example Inventory and Playbook
------------------------------

This repository contains a sample Ansible inventory and playbook.

The inventory file `sonarinventory` is setup to create one instance of the toolkit.

 - 'sonar.example.edu.au' On this machine the package 'perfsonar-toolkit' is
 installed along with 'certbot' to setup SSL certificates.

To run the playbook to install perfSONAR:

> ansible-playbook  -i sonarinventory -l perfsonarbuild -t perfsonarbuild sonarnodes.yml

Role Variables
--------------

The following variables should be set prior to running the role.

- vars/certbot.yml - Let's Encrypt Certbot configuration
  - certbot_email: contact email address for Let's Encrypt


These files will need customising for your site:
- sonarinventory (set the domain name, IP address and user)

Post Installation
------------------
The following notes and links will assist in getting started with perfSONAR.

perfSONAR Lookup Service Directory: http://stats.es.net/ServicesDirectory/
This site can be used to locate other perfSONAR sites available for testing network
connectivity. For some documentation on how to use this feature and Testing Etiquette, please refer to: https://docs.perfsonar.net/manage_locating_hosts.html

Managing users for web access: https://docs.perfsonar.net/manage_users.html
Use this page to find out how to add and remove users from the Web Interface.
This access is required to manually schedule regular tests.

Adding new tests: https://docs.perfsonar.net/manage_regular_tests.html
This page contains detailed information on the types of test available and how to schedule them.

Logs: These can be accessed via the website at: https://perfsonar.massive.cloud.monash.edu/toolkit/auth/admin/logs/
You need to have a web account to view them.

Viewing scheduled tests: https://docs.perfsonar.net/pscheduler_client_schedule.html
The command "pschedule monitor" displays past, current and future tests.

Backing up the data: https://docs.perfsonar.net/multi_ma_backups.html
Two databases are used: cassandra and PostgreSQL. This link contains instructions on how to back up both.

Author Information
------------------

Jay van Schyndel - Monash eResearch Centre
