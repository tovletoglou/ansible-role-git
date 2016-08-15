# Ansible Role: git on CentOS 7

Installs git **2.9.x** on CentOS 7 using `ius` repository or build it from source.

## Requirements

Tested CentOS 7

## Get started

If you came here and you have no idea where to start and **the only think you worry is git 2.9.x on Centos 7**  select the following commands and paste it on your terminal.

    # Install EPEL repository (need it for ansible)
    sudo yum install -y epel-release
    # Install Ansible
    sudo yum install -y ansible
    # Install git
    sudo yum install -y git
    # Create Ansible hosts file mapped on localhost
    sudo echo "localhost ansible_connection=local" >> /etc/ansible/hosts
    # Create you first playbook
    mkdir ~/ansible-playbook
    echo "---

    - hosts: all
      become: yes
      roles:
        - ansible-role-git" > ~/ansible-playbook/git-playbook.yml
    # Clone this project (it's an ansible role)
    git clone https://github.com/tovletoglou/ansible-role-git.git ~/ansible-playbook/roles/ansible-role-git
    # Run the playbook
    ansible-playbook ~/ansible-playbook/git-playbook.yml
    # Test git
    git --version
    # Enjoy

## Role Variables

Available variables are listed below, along with default values `defaults/main.yml`

**Choose how to install git** (true = source | false = IUS repo)

    git_install_from_source: false

**Update git for IUS repo every time you run this role** (present | latest).

    git_update: latest

The following settings apply only when you setup git from source.

**Remove git installed with yum** (true | false).

    git_remove: false

**Git version should be an exact version and not a branch.**

    git_version: 2.9.3

**Install git documentation** (true | false)

    git_documentation: true

## Dependencies

None

## Example Playbook

Installed with galaxy.ansible `ansible-galaxy install tovletoglou.git`

    ---

    - hosts: all
      roles:
        - { role: tovletoglou.git }

Installed as a playbook git submodule  `git clone https://github.com/tovletoglou/ansible-role-git.git playbook/roles/ansible-role-git`

    ---

    - hosts: all
      roles:
        - { role: ansible-role-git }

Sending custom vars

    ---

    - hosts: all
      roles:
        - { role: tovletoglou.git }
      vars:
        git_version: 2.9.3

## License

MIT

## Author Information

Apostolos Tovletoglou [ansible-role-git](https://github.com/tovletoglou/ansible-role-git)
