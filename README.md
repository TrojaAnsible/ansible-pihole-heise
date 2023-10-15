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
|docker_dirs1|list of installation sub-directory|no|
|docker_dirs2|list of installation sub-directory|no|
|pihole_env| template name|pihole.env|no|
|timezone|Timezone| Europe/Vienna|no|
|pihole_image|pihole image|pihole/pihole:latest|no|
|pihole_myconfig|pihole config|99-my-config.conf|no|
|pihole_script|start/backup script|pihole|no|
|dnscrypt_image|dnscrypt-proxy image|klutchell/dnscrypt-proxy:2.1.5|no|
|stubby_image|stubby image|juharov/stubby-vance-arm:latest|no|
|vault_pihole_web_password|pihole web password|no default|yes|


Dependencies
------------


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ansible-pihole-heise }

License
-------

This project is licensed under the Attribution-NonCommercial-ShareAlike 4.0 International License - see the [LICENSE.md](LICENSE.md) file for details

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
