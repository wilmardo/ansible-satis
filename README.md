Satis Ansible Role
==================

[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-HanXHX.satis-blue.svg)](https://galaxy.ansible.com/HanXHX/satis/) [![Build Status](https://travis-ci.org/HanXHX/ansible-satis.svg?branch=master)](https://travis-ci.org/HanXHX/ansible-satis)

This is an ansible role for installing satis through composer.

Requirements
------------

- php
- composer
- git

Role Variables
--------------

### System

- `satis_user`: Username which satis is installed as, is created when non existing
- `satis_group` Usergroup which satis is installed as, is created when non existing
- `satis_user_home` Location of the userhome of the satis user

### Install

- `satis_installation`: Install directory
- `satis_config_file`: Satis configuration file location (contains `satis_json` config)
- `satis_build_dir`: Build directory
- `satis_manage_cron`: (bool) manage crontab 
- `satis_version`: Satis version to install (alpha for latest pre-release, dev for master branch)

### Configuration

- `satis_composer_ignore_secure_http`: (bool) If set to true composer only allows HTTPS urls to be downloaded ([docs](https://getcomposer.org/doc/06-config.md#secure-http))
- `satis_json`: (hashlist) Gets converted to JSON format ([to_nice_json](http://docs.ansible.com/ansible/latest/playbooks_filters.html#filters-for-formatting-data)) and placed as satis config file, satis.json. Every variable out of the docs can be used ([docs](https://getcomposer.org/doc/articles/handling-private-packages-with-satis.md)).
Define the variables as YAML, see the following example.
````yaml
satis_json:
  name: "satis repository"
  homepage: "http://localhost/"
  repositories:
    - type: "composer"
      url: "https://packagist.org"
  require:
    symfony/polyfill-apcu: "*"
  require-all: true
  require-dependencies: true
  require-dev-dependencies: false
  archive:
    whitelist: []
    blacklist: []
    directory: dist
    format: zip
    skip-dev: false
  providers: false
  config: {}
  notify-batch: /downloads/
````

Dependencies
------------

None.

Example Playbook
----------------

See [test playbook](tests/test.yml).

License
-------

MIT

Author Information
------------------

- Twitter: [@hanxhx_](https://twitter.com/hanxhx_)
