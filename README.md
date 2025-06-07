Role Name
=========

setup-i3

Installs Xfce and lightdm as the display manager.

Requirements
------------


Role Variables
--------------

# user list whose purpose is to make sure the gecos field is update so
# the name properly appears under lightdm's user dropdown
setup_i3_gui_users:
  - username:
    gecos:
---
setup_i3_pkgs:
  - lightdm
  - lightdm-gtk-greeter
  - dbus
  - i3

setup_i3_svcs:
  - lightdm

setup_i3_sysrc_directives:
  - name: lightdm_enable
    value: "YES"
  - name: dbus_enable
    value: "YES"

#command to update pixbuf cache
setup_i3_pixbuf_update_path: /usr/local/bin/gdk-pixbuf-query-loaders

#command to update mime database
setup_i3_mime_db_path: /usr/local/bin/update-mime-database

#location of mime database
setup_i3_mime_data_path: /usr/local/share/mime

# location of user's i3 config file
setup_i3_user_config_path: .config/i3/config

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      vars:

        setup_i3_gui_user:
          - username: rich
            gecos: "Rich"

      roles:
         - name: setup-i3

License
-------

BSD

Author Information
------------------

Rich O'Hara

