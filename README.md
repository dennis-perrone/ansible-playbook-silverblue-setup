# Silverblue Setup Playbook

## Overview

An Ansible playbook to set up a vanilla Fedora Silverblue box.

## Steps

- On a vanilla box, run `mkdir -p $HOME/temp; cd $_`
- Enter `git clone https://github.com/dennis-perrone/ansible.git`
- Change into the Ansible directory
- Create a virtual environment by entering `python3 -m venv .`
- Run `bin/pip3 install ansible`
- Execute playbook by entering `bin/ansible-playbook -i inventory -K --ask-vault-pass site.yml` 

## Tags

This playbook is set up with tags to be able to run specific tasks or specific roles.

## Roles

- `common`: Includes the entire `common` role:
    - `distrobox`: Creates Distrobox directory and copies config file.
    - `git`: Sets up git global configurations and clone repositories.
    - `home_dir`: Sets up XDG user directory defaults.
    - `main`: Generates a new SSH key and serves as jumping point for other files.
    - `samba`: Sets up the local Samba share and credentials.
    - `vscode`: Sets up VSCode/VSCodium defaults and extensions.
- `flatpaks`: Adds Flathub for a remote repository. Removes some default Flatpaks and installs Flatpaks that I use.
- `gnome_settings`: Sets up Gnome extensions and defaults.
- `layered_packages`: Sets up layered packages and removes some default ones.
- `os_upates`: Configures rpm-ostree with some sane defaults.