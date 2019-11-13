factorio-manager
================
Simple server management script for running multiple simultaneous servers.

Installation
------------

    git clone https://github.com/trumank/factorio-manager.git
    cd factorio-manager
    makepkg -eis

Example Usage
-------------

    sudo systemctl start factorio-manager@new-server.service #it's that easy!

Configuration
-------------
Server config files reside in `/etc/factorio-manager/servers/<name>/config`
Until I get around to it, only server version can be configured.

Server schedule
---------------
Servers can be reset by sending a USR1 signal to the factorio-manager process. Upon reset, the server archives the old map, generates a new one, and starts again

Data
--------
Non-configuration data is stored under `/var/lib/factorio-manager/servers/`

