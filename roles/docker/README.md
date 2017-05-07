# Docker

An Ansible role that installs the latest version of Docker CE on Ubuntu based on the official installation instructions.

Installs docker-py for other Ansible scripts to run.

Changes the docker.socket systemd unit file to ensure the network share is mounted before starting Docker
