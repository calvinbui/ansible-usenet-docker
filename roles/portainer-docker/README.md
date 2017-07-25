# Portainer Docker

Portainer is a lightweight management UI which allows you to easily manage your different Docker environments (Docker hosts or Swarm clusters).

Portainer is a little special on how run configure NGINX to reverse proxy it: https://portainer.readthedocs.io/en/stable/faq.html#how-can-i-configure-my-reverse-proxy-to-serve-portainer. These special things are implemented in the NGINX and Let's Encrypt playbook using `if` statements.
