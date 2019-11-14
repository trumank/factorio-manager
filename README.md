factorio-manager
================
Simple server management script for running multiple simultaneous servers.

Installation
------------
Currently there is only a PKGBUILD to be used on Arch, but it shouldn't be hard to build for other systems.

    git clone https://github.com/trumank/factorio-manager.git
    cd factorio-manager
    makepkg -eis

Example Usage
-------------

    sudo systemctl start factorio-manager@new-server.service #it's that easy!

Configuration
-------------
Server config files reside in `/etc/factorio-manager/servers/<name>/`

    # config
    version=stable, experimental, or specific version
    bind=[ADDRESS:]PORT
    rcon_bind=[ADDRESS:]PORT
    rcon_password=rcon password

The following are automatically loaded if present:
- map-gen-settings.json
- map-settings.json
- server-settings.json
- server-whitelist.json

A scenario named "scenario" placed in the config directory will be used to generate all new maps if present.

Server schedule
---------------
Servers can be reset by sending a USR1 signal to the factorio-manager process. Upon reset, the server archives the old map, generates a new one, and starts again

An easy way to reset a server on a schedule is to use the systemd reset unit on a timer:

    # /etc/systemd/system/factorio-manager-reset@<server name>.timer
    [Unit]
    Description=Factorio weekly reset

    [Timer]
    OnCalendar=weekly

    [Install]
    WantedBy=timers.target

Data
----
Maps and archived data are stored under `/var/lib/factorio-manager/servers/<name>`

