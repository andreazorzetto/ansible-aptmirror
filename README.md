Aptmirror
======

Install and configure an aptmirror server that can mirros software from:
- Default Ubuntu mirrors:
- PPAs
- External repositories

This role can be used together with [ansible-apt-repo](https://galaxy.ansible.com/andreazorzetto/Apt-Mirror-Client/) for the client side.

Tasks
======

- Installing software: apt-mirror, proftpd
- Fixing proftpd init script
- Configuring FTP anonymous user
- Configuring crontab for aptmirror (once a month)
- Generating mirror list configuration
- Folders and key setup on FTP share
- Downloading cache and installing repos keys

Description
======

All the repos to install are specified into the var file.

For example, here is how to mirror ubuntu default repos a ppa and an external repo:

```
repos:
  - title: ubuntu
    source: true
    proto: http
    url: archive.ubuntu.com/ubuntu
    distro:
      - trusty
      - trusty-security
      - trusty-updates
    components:
      - main
      - restricted
      - universe
      - multiverse
    gpgkey: 40976EAF437D05B5

  - title: ondrej
    source: true
    proto: http
    url: ppa.launchpad.net/ondrej/php/ubuntu
    distro:
      - trusty
    components:
      - main
    gpgkey: E5267A6C

  - title: grafana
    source: false
    proto: https
    url: packagecloud.io/grafana/stable/debian
    distro:
      - wheezy
    components:
      - main
    keyurl: https://packagecloud.io/gpg.key
```  
