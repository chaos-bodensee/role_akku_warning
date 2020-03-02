[![ansible-galaxy: do1jlr.akku_warning](https://raw.githubusercontent.com/chaos-bodensee/role_akku_warning/master/.github/galaxy.svg?sanitize=true)](https://galaxy.ansible.com/do1jlr/akku_warning) [![Build Status](https://travis-ci.org/chaos-bodensee/role_akku_warning.svg?branch=master)](https://travis-ci.org/chaos-bodensee/role_akku_warning) [![MIT License](https://raw.githubusercontent.com/chaos-bodensee/role_akku_warning/master/.github/license.svg?sanitize=true)](https://github.com/chaos-bodensee/role_akku_warning/blob/master/LICENSE)

 akku warning (ansible role)
==========================

This ansible warning will install an bash Script, that will be executet every 3 minutes.

If your batterie is under 25 percent, it will start warning you.

This role is tested with the [i3 - improved tiling wm](https://i3wm.org/), but probably will work on all window managers!


 Permissions
--------------
This role requires superuser privileges for the following tasks:
  - copy bashscript to ``{{ akku_warning.script_dest }}``
  - copy multimedia to ``{{ akku_warning.multimedia.sound_dest }}``
  - install packages like ``zenity`` and ``mpv``
  - install cronjob to /etc/crontab for user ``{{ akku_warning.user }}``

 Variables:
-----------
```yaml
akku_warning:
  user: "{{ ansible_user_id }}"

  script_dest: '/opt/akku.sh'

  # should we support a multimedia warning
  multimedia_support: true
  multimedia:
    sound_src: 'files/low_battery.m4a'
    sound_dest: '/opt/low_battery.m4a'

  install_and_enable_cronie: true

  manage_packages: true

  display_address: ':0.0'

# should we use a simple versionscheck (true is recomended)
submodules_versioncheck: false
```

 Installation and Usage
------------
### install with galaxy:
```bash
ansible-galaxy install do1jlr.akku_warning
```

### example playbook with galaxy
```yaml
---
- hosts:
  roles:
    - do1jlr.akku_warning
```

### installation via git
```bash
# download this role into your roles directory
git clone https://github.com/roles-ansible/role_akku_warning.git
```

### example playbook
```yaml
---
- name: install akku_warning
  hosts: localhost
  tags:
   - akku_warning
  roles:
    - role_akku_warning
  vars:
    submodules_versioncheck: true
```

 Missing something?
----------------
Please feel free to open a [github](https://github.com/roles-ansible/role_akku_warning.git) Issue or Pull-Request. Thanks <3

 Testing
---------
This role is tested with [these github-action](https://github.com/search?q=topic%3Acheck-ansible+topic%3Agithub-actions+org%3Aroles-ansible&type=Repositories) tests for different versions of debian and ubuntu. Linting is tested via travis-ci.
If you want to find out more about our tests, please have a look at the github marketplace.

| test status | Github Marketplace |
| :---------  | :----------------  |
| [![Travis Build Status](https://travis-ci.org/roles-ansible/role_akku_warning.svg?branch=master)](https://travis-ci.org/roles-ansible/role_akku_warning) | [.travis.yml](https://github.com/roles-ansible/role_akku_warning/blob/master/.travis.yml) |
| [![Ansible check debian:stable](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:stable/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Astable%22) | [ansible test with debian stable](https://github.com/marketplace/actions/check-ansible-debian-stable) |
| [![Ansible check debian:sid](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:sid/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Asid%22) | [ansible test with debian sid](https://github.com/marketplace/actions/check-ansible-debian-sid) |
| [![Ansible check debian:buster](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:buster/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Abuster%22) | [ansible test with debian buster](https://github.com/marketplace/actions/check-ansible-debian-buster) |
| [![Ansible check debian:jessie](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:jessie/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Ajessie%22) | [ansible test with debian jessie](https://github.com/marketplace/actions/check-ansible-debian-jessie) |
| [![Ansible check debian:stretch](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20debian:stretch/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+debian%3Astretch%22) | [ansible test with debian stretch](https://github.com/marketplace/actions/check-ansible-debian-stretch) |
| [![Ansible check ubuntu:latest](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:latest/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Alatest%22) | [ansible test with ubuntu latest](https://github.com/marketplace/actions/check-ansible-ubuntu-latest) |
| [![Ansible check ubuntu:bionic](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:bionic/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Abionic%22) | [ansible test with ubuntu bionic](https://github.com/marketplace/actions/check-ansible-ubuntu-bionic) |
| [![Ansible check ubuntu:disco](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:disco/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Adisco%22) | [ansible test with ubuntu disco](https://github.com/marketplace/actions/check-ansible-ubuntu-disco) |
| [![Ansible check ubuntu:eoan](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:eoan/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Aeoan%22) | [ansible test with ubuntu eoan](https://github.com/marketplace/actions/check-ansible-ubuntu-eoan) |
| [![Ansible check ubuntu:focal](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:focal/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Afocal%22) | [ansible test with ubuntu focal](https://github.com/marketplace/actions/check-ansible-ubuntu-focal) |
| [![Ansible check ubuntu:trusty](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:trusty/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Atrusty%22) | [ansible test with ubuntu trusty](https://github.com/marketplace/actions/check-ansible-ubuntu-trusty) |
| [![Ansible check ubuntu:xenial](https://github.com/roles-ansible/role_akku_warning/workflows/Ansible%20check%20ubuntu:xenial/badge.svg)](https://github.com/roles-ansible/role_akku_warning/actions?query=workflow%3A%22Ansible+check+ubuntu%3Axenial%22) | [ansible test with ubuntu xenial](https://github.com/marketplace/actions/check-ansible-ubuntu-xenial) |
