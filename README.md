# Usenet Docker Ansible

## Run

`ansible-playbook site.yml -vv`

## System Requirements

-   1.5GB of RAM
-   2 CPU minimum
-   Ubuntu 16.04 and onward
-   16GB of space

## About

This is an Ansible playbook which installs my Usenet services in Docker containers on a Ubuntu server.

The playbook:

-   Performs a simple setup of a new host (dist-upgrade and open-vm-tools)
-   Sets up a NFS mount
-   Installs Docker
-   Set up Docker user-defined network
-   Installs NZBGet, Transmission, NZBHydra, Sonarr and CouchPotato
-   Installs NGINX with LDAP authentication to proxy those services
-   Installs Muximux to provide easy access to those services
-   Generate certificates using Let's Encrypt on the Docker host (not container) and links the certificates to the sites

## Commands

See Docker stats: `docker stats --format "table {{.Name}}\t{{.CPUPerc}}\t{{.MemPerc}}\t{{.MemUsage}}\t{{.NetIO}}\t{{.BlockIO}}\t{{.PIDs}}"`

## Passwords

SSH Password is stored in group_vars/vault.yml

Set vault password through ANSIBLE_VAULT_PASSWORD_FILE=~/.vault_pass.txt

## Gotchas

-   The NZBGet and Transmission Docker images change permissions on the NFS file share. The freenas-permissions role prevents changes those permissions back and the NZBGet/Transmission role removes that command as well

## TODO

-   Auto-upgrade images using Watch Tower. Will have to combine with gotcha's above. (transform into scripts?)
-   401 Error Page
