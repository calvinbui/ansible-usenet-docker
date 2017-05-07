# NGINX Docker

An Ansible role which installs NGINX with the LDAP module

All files are read-only to the container

The services in usenet-services are from services.yml

## Files

-   proxy-settings: basic proxy_pass variables
-   ldap-config: LDAP settings
-   ldap-prompt: put this LDAP login is required
-   usenet-services: the services to proxy through
-   vms: proxies my Milestone video management web server

[https://hub.docker.com/r/dweomer/nginx-auth-ldap/](https://hub.docker.com/r/dweomer/nginx-auth-ldap/)
