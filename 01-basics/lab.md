# Lab 1

## Ansible Intro

We will use Ansible in this course as a configuration management tool. There are
dozens of configuration management tools out there but we've chosen Ansible as
one of the simplest one to get started with.

You can run Ansible from your laptop directly in case you have Linux or MacOS.
In case you have Windows, it's recommended to use
[VirtualBox](https://www.virtualbox.org/wiki/Downloads) running Ubuntu as guest VM.

## Task 1. Install Ansible

For Linux or OS X, I recommend to use Python virtual env:

    python3 -m venv ~/ansible-venv
    ~/ansible-venv/bin/pip install ansible==2.11.6
    ~/ansible-venv/bin/ansible --version

Last command should print something like

    ansible [core 2.11.6]

Then, add this line to your `~/.profile` file (if the file is missing, create it)
so you can use 'shorter' commands:

    PATH="$HOME/ansible-venv/bin:$PATH"

Logout and log in again. Now this command should also work:

    ansible --version

## Task 2. Test access to your network device

Ansible uses ssh for device management. If you can't ssh to device, Ansible can't either.

Try:

    ssh <username>@<managed_host>

You should be able to login.

Note: By default ssh is disabled on Cisco devices. To enable it you need to execute few commands.

## Task 3. Create Ansible inventory

Create inventory file in project folder.

Create group "routers":

    [routers]
    <ip_of_your_device>

## Task 4. Create Ansible configuration file

Create Ansible configuration file in project folder.

Docs: https://docs.ansible.com/ansible/latest/reference_appendices/config.html

Parameters that should be specified:

    - inventory
    - ask_pass (if not using ssh keys)
    - gathering

## Task 5. Ansible Ad-Hoc commands

While Ansible using Ad-Hoc commands not the best practice to use them, sometimes they can be usefull for gathering info from devices.

Write commands that will collect the following from group "routers":

    - list of IP addresses
    - arp table
    - routing table

## Hints

Specify ansible_user for every device you connecting. You won't need to specify username every time after that.
