# Lab 4

In this lab we will configure OSPF on a pair of routers.

## Task 1. Basic OSPF setup

Create Jinja2 template that will configure OSPF on routers. Put management interface to area 0.

Create a task in playbook that will configure routers using created Jinja2 template:

    ios_config:
      src: ....j2

## Task 2. Create Loopback interfaces

Create `loopbacks` variable that describes additional interfaces for each router:

    loopbacks:
      lo0:
        ip: 10.1.0.1/26
        description: Some text  # Optional
        ospf_area: 2  # Optional. Don't enable OSPF if missing
      lo1:
        ip: 10.2.0.1/27
      lo2:
        ip: 10.3.0.1/22
        ospf_area: 32
      lo3:
        ...
      lo4:
        ...

Based on provided info, create two Jinja2 templates:
  - interface configuration
  - `network` statements under `router ospf` for OSPF-enabled interfaces

Create 2 tasks in playbook that will configure routers using created Jinja2 templates.

## Task 3. Setup OSPF authentication

Create Jinja2 template that will configure md5 OSPF authentication on management interface.

Use Ansible Vault to store the password in your repo. Update your `ansible.cfg` with vault password file location. Vault password file should be outside of your repo.

Create a task in playbook that will configure router using created Jinja2 template.

## Task 4. Print some OSPF info

Parse the output of `show ip ospf neighbor` and print all OSPF neighbors IDs.

Parse the output of `show ip route ospf` and print the number of OSPF learned routes.

## Expected result

All configuration should be done with single command without any parameters:

    ansible-playbook lab04.yaml
