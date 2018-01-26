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
- `satis_config_file`: Satis configuration file location
- `satis_build_dir`: Build directory
- `satis_manage_cron`: (bool) manage crontab 
- `satis_version`: Satis version to install (alpha for latest pre-release, dev for master branch)

### Configuration

- `satis_repo_name`: (string) Repository name
- `satis_repo_homepage`: (string) Repository URL
- `satis_repos`: (hashlist)
- `satis_require`: (optional) Key/value hash with repositories version
- `satis_skip_dev`: (bool)
- `satis_composer_ignore_secure_http`: (bool) Composer secure-http setting ([docs](https://getcomposer.org/doc/06-config.md#secure-http))
- `satis_require_all`: (bool)
- `satis_require_dependencies`: (bool)
- `satis_require_dev_dependencies`: (bool)
- `satis_archive`: (optional) Can be used to set all the Satis archive options [docs](https://getcomposer.org/doc/articles/handling-private-packages-with-satis.md#downloads) Define like the JSON but in YAML so no braces etc [example](defaults/main.yml)
- `satis_providers`: (optional) When set to true each package will be dumped into a separate include file which will be only loaded by composer when the package is really required. [docs](https://getcomposer.org/doc/articles/handling-private-packages-with-satis.md#other-options)
- `satis_config`: (optional) Can be used to set composer options [docs](https://getcomposer.org/doc/articles/handling-private-packages-with-satis.md#downloads)
- `satis_notify_batch`: (optional) specify a callback URL [docs](https://getcomposer.org/doc/articles/handling-private-packages-with-satis.md#downloads)

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
