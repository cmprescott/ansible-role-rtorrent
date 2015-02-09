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
ip_num: 127.0.0.1
ip_dns: rakshasa.no
bind_num: 127.0.0.1
bind_dns: rakshasa.no
port_range: 49164-49164
port_random: "no"
scgi_port: 127.0.0.1:5000 
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
schedule_watch_directory: watch_directory,5,5,load_start=
schedule_untied_directory: untied_directory,5,5,stop_untied=
schedule_low_diskspace: low_diskspace,5,60,close_low_diskspace=100M
schedule_ratio: ratio,60,60,"stop_on_ratio=200,200M,2000"
schedule_ip_tick: ip_tick,0,1800,ip=rakshasa
schedule_bind_tick: bind_tick,0,1800,bind=rakshasa
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

