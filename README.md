Role Name
=========

install pihole container with dnscrypt-proxy and stubby

Requirements
------------


Role Variables
--------------
| defaults variable | description |default value|mandatory|
|-------------------|-------------|-------------|---------|
|app_user|user for the install directory| pihole|no|
|docker_home|base install directory| /opt/docker|no|
|docker_dirs1|list of installation sub-directory|pihole/etc-pihole|no|
|docker_dirs2|list of installation sub-directory||no|
|pihole_env| template name|pihole.env|no|
|timezone|Timezone| Europe/Vienna|no|
|pihole_image|pihole image|pihole/pihole:latest|no|
|pihole_myconfig|pihole config|99-my-config.conf|no|
|pihole_script|start/backup script|pihole|no|
|dnscrypt_image|dnscrypt-proxy image|klutchell/dnscrypt-proxy:2.1.5|no|
|stubby_image|stubby image|juharov/stubby-vance-arm:latest|no|
|vault_pihole_web_password|pihole web password|no default|yes|
|CONTAINER_NET|subnet for the three containers|172.25.0|no|
|REV_SERVER|Enable DNS conditional |"true"|no|
|REV_SERVER_DOMAIN|local DNS domain|"fritz.box"|no|
|REV_SERVER_TARGET|local DNS server|"{{ hostvars[inventory_hostname]['ansible_default_ipv4']['gateway'] }}"|no|
|REV_SERVER_CIDR|local CIDR network notation|"{{ (ansible_default_ipv4.network + '/' + ansible_default_ipv4.netmask) &#124; ansible.utils.ipaddr('network/prefix') }}"|no|
|DNSCRYPT_CONF|dnscrypt config file|./config/dnscrypt-proxy.toml|no|
|STUBBY_CONF|stubby config file|./config/stubby-quad9.yml|no|


The variables docker_dirs1 docker_dirs2 create directory with two different groupnames. Groupname docker_dirs1 is used to align host group name with container group id


Note
------------

The default values for ```REV_SERVER_TARGET``` and ```REV_SERVER_CIDR``` are set by ansible. It is assumed, that the default gateway is your router and upstream DNS ip.
```
REV_SERVER_TARGET: "{{ hostvars[inventory_hostname]['ansible_default_ipv4']['gateway'] }}"
REV_SERVER_CIDR: "{{ (ansible_default_ipv4.network + '/' + ansible_default_ipv4.netmask) | ansible.utils.ipaddr('network/prefix') }}"
```
If you have a different setup, you need to overwrite this in the role vars.


Dependencies
------------

A Docker installation.

e.g. role creates following setup [docker-pihole-dot-doh](https://github.com/plix1014/docker-pihole-dot-doh)


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters):

```
  tasks:
    - include_role:
        name: ansible-pihole-heise
      vars:
        timezone: Europe/Vienna
        stubby_image: "juharov/stubby-vance-arm:latest"
        REV_SERVER_DOMAIN: "fritz.box"
```


License
-------

This project is licensed under the Attribution-NonCommercial-ShareAlike 4.0 International License - see the [LICENSE.md](LICENSE.md) file for details

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
