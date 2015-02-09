rtorrent
=====

This role installs and configures rtorrent. The user can specify any rtorrent configuration parameters they wish. 

Requirements
------------

This role requires Ansible 1.4 or higher and Ubuntu.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows.

```
# -------------
# bandwidth settings
# -------------
min_peers: 40
max_peers: 100
min_peers_seed: 10
max_peers_seed: 50
max_uploads: 15
download_rate: 0
upload_rate: 0
# -------------
# network settings
# -------------
port_range: 49164-49164
port_random: "no"
# -------------
# torrent settings
# -------------
check_hash: "no"
use_udp_trackers: "yes"
encryption: allow_incoming,enable_retry,prefer_plaintext
dht: auto
dht_port: 6881
peer_exchange: "yes"
# -------------
# directory settings
# -------------
directory_download: ~/rtorrent/download
directory_session: ~/rtorrent/.session
directory_watch: ~/rtorrent/watch
# -------------
# schedule settings
# -------------
schedule_watch_directory: watch_directory,5,5,load_start={{ directory_watch }}/*.torrent
schedule_untied_directory: untied_directory,5,5,stop_untied=
other_settings:
    - scgi_port = 127.0.0.1:5000 
```

Examples
========

1) Install rtorrent with default settings

    - hosts: all
      roles:
      - role: rtorrent


2) Install rtorrent with custom settings

    - hosts: all
      roles:
      - role: rtorrent
        min_peers: 0
        max_peers: 1000


Dependencies
------------

None

License
-------

BSD

Author Information
------------------

- Original : Prescott Chris

