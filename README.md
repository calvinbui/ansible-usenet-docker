# Usenet Docker Ansible

## Run

`ansible-playbook site.yml -vv`

## System Requirements

-   1.5GB of RAM
-   2 CPU minimum
-   Ubuntu 16.04 and onward
-   16GB of space

## About

This is an Ansible playbook which installs my Usenet services in Docker containers on a Ubuntu server. Each Usenet service is an Ansible role.

The following roles are available:

-   NZBGet
-   Transmission
-   NZBHydra
-   Sonarr
-   Radarr
-   CouchPotato
-   Muximux
-   Organizr
-   Portainer

The playbook does the following:

-   Performs a simple setup of a new host (dist-upgrade and open-vm-tools)
-   Sets up a NFS mount
-   Installs Docker
-   Set up Docker user-defined network
-   Installs NZBGet, Transmission, NZBHydra, Sonarr Radarr and/or CouchPotato
-   Installs NGINX with LDAP authentication to proxy those services
-   Installs Organizr or Muximux to provide easy access to those services
-   Generate certificates using Let's Encrypt on the Docker host (not container) and links the certificates to the sites
-   Add backstroke.us links to crontab
-   Installs Watchtower to update images automatically

## Commands

See Docker stats: `docker stats --format "table {{.Name}}\t{{.CPUPerc}}\t{{.MemPerc}}\t{{.MemUsage}}\t{{.NetIO}}\t{{.BlockIO}}\t{{.PIDs}}"`

## Passwords

SSH Password is stored in group_vars.

Set vault password through ANSIBLE_VAULT_PASSWORD_FILE=~/.vault_pass.txt

## Automatically Updating Images

[Watchtower](https://hub.docker.com/r/v2tec/watchtower/) is used to monitor running Docker containers and watch for changes to the images that those containers were originally started from. If Watchtower detects that an image has changed, it will automatically restart the container using the new image.

For problematic images that have been forked and edited (NZBGet and Transmission), [Backstroke](https://backstroke.us) keeps their repositories up to date with their respective upstreams. A cron job is created to lookup new changes and raise pull requests if there are any changes. From here, Docker Hub will automatically build the new image as it is a service linked in GitHub.

## Testing

1.  Update the `vault.txt` file
2.  Run `vagrant up`

## TODO

-   401 Error Page, most likely have to use official NGINX LDAP Auth.
-   Move variables so that single roles can run without depending on other role variables
