# Lab 3

## Task 1. A bit more advanced playbook

Create playbook that will configure basic device settings for single router:

    - hostname
    - ntp servers
    - syslog servers
    - service password-encryption

## Task 2. Save config if needed

If some changes were done by playbook - save config. Do nothing if no changes were made.

## Task 3. Backup your config

Create config backup before applying any changes to the device.

Backup files should be in folder "ios_backups" with names "\<device_hostname\>.backup"

## Task 4. Create access list for vty lines

Create extended access-list 101 to allow ssh connections to VTY lines.

Ansible server IP should be permitted in the first line of this acl. Ansible server IP should come from variables, destination IP also should come from variables, best options would be to reuse ansible_host from inventory.

Don't allow any changes in access list if the first line doesn't allow connections from Ansible server. In this case, just print a message with explanation. Example:

    Acl:
    - deny ip any any
    - permit tcp host {{ ansible_server }} host {{ ansible_host }} eq 22
    Msg:
    Skipping ACL change because of possible ssh lock.

## Task 5. Collect additional info about your devices

With the help of ios_facts module create a report about your network devices. Reports should be in "reports/\<device_name\>.info".

Content of report:

    Hostname: XXX
    Model: XXX
    IOS type: XXX
    IOS version: XXX
    Serial number: XXX

## Expected result

If you didn't do any changes with variables or playbook, command

    ansible-playbook lab03.yaml

shouldn't do any changes.

Most probably you should adjust commands in playbook to make it idemponent.
