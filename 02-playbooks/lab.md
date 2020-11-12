# Lab 2

## Task 1. Simple playbook

Create playbook that will configure basic device settings for single router:

    - hostname
    - ntp servers
    - syslog servers
    - service password-encryption

## Task 2. Variables

Create file group_vars/all.yaml

Write there variables for:

    - ntp servers
    - syslog servers

Create file host_vars/\<name_of_your_device\>.yaml

Write there variables for:

    - hostname

## Task 3. Playbook with variables

Put variables into your playbook from task 1. Apply plays to group "routers", can be 1 or 2 devices in group, based on your resources.

## Task 4. Make your playbook idemponent

If you didn't do any changes with variables or playbook, command

    ansible-playbook lab02.yaml

shouldn't do any changes.

Most probably you should adjust commands in playbook to make it idemponent.
