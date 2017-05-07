# NZBGet Docker

An Ansible role that installs NZBGet on Docker.

The LinuxServer image changes permissions on the Downloads folder to abc:abc.

There is a task which runs a command to remove that command from the startup scripts.

Pair this with the FreeNAS Permissions role to also change the permission back to what they used to be.

[https://hub.docker.com/r/linuxserver/nzbget/](https://hub.docker.com/r/linuxserver/nzbget/)
