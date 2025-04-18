## Ansible Role: Domain Join for Debian Hosts

This Ansible role automates the process of setting up Debian's basic operating system settings.

## Actions Performed

The role performs the following actions:

1. Update operating system.
2. Install preferred tools and utilities.
3. Set default text editor.
4. Set timezone.
5. Configure timekeeping.
6. Configure firewall.

## Setup Instructions

### Clone Repository

Clone the project into the roles directory of your Ansible Controller.

```bash
git clone https://github.com/twobyteblog/ansible_baseline.git
```

### Variables

Within ```vars/main.yml``` fill in the following variables.

```bash
# Time keeping.
timezone: UTC
ntp_package_name: chrony
ntp_service_name: chronyd

## Baseline packages installed on all hosts.
packages: [ sudo, vim, gcc, make, curl, unzip, rsync, iftop, iotop, htop, tcpdump, mtr, git, dnsutils, acl ]

## Default text editor.
default_editor: /usr/bin/vim.basic
```

### Playbook

Create a playbook which runs this role. This role requires become privileges.

```
- hosts: all
  roles:
    - role: ansible_baseline
      become: yes
```