# README

This is a template for provisioning (groups of) remote hosts.

## Disclaimer

In production, use ansible vault instead of storing credentials in inventory files.

## directory layout

- see [best practices section](https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html#directory-layout)

## configure the inventory

- If you prefer to use ssh keys to connect to remotes, fill in the relevant data in `hosts-ssh.ini` and continue to the [ssh section](#ansible-ssh-via-key-pair).
- If you prefer to access remotes via password, fill in the relevant data in `hosts-pass.ini` and continue to the [password section](#ansible-ssh-via-password).

## ansible ssh via key-pair

- 1: Create ssh keys (provisioner) `ssh-keygen -t rsa -b 4096`
- 2: Trust ssh public key on remotes (run on provisoner) `ssh-copy-id remote_user@remote_host`
- 3: Run `ansible-playbook site.yml -i hosts-ssh.ini`

## ansible ssh via password

- 1: Install on provisioner (host): `sudo apt install sshpass`
- 2: Add the remotes to the `known_hosts` on the control node or run: `export ANSIBLE_HOST_KEY_CHECKING=False`
- 3: Run `ansible-playbook site.yml -i hosts-ssh.ini`
