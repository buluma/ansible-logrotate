# Ansible Logrotate Role

[![Build Status](https://travis-ci.org/buluma/ansible-logrotate.svg?branch=master)](https://travis-ci.org/buluma/ansible-logrotate)
[![GitHub Tags](https://img.shields.io/github/tag/buluma/ansible-logrotate.svg)](https://github.com/buluma/ansible-logrotate)
[![GitHub Stars](https://img.shields.io/github/stars/weareinteractive/ansible-logrotate.svg)](https://github.com/weareinteractive/ansible-logrotate)

> `logrotate` is an [ansible](http://www.ansible.com) role which:
>
> * installs logrotate
> * adds logrotate scripts

## Installation

Using `ansible-galaxy`:

```
$ ansible-galaxy install buluma.logrotate
```

Using `requirements.yml`:

```
- src: franklinkim.logrotate
```

Using `git`:

```
$ git clone https://github.com/buluma/ansible-logrotate.git buluma.logrotate
```

## Dependencies

* Ansible >= 1.9

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```
# logrotate_scripts:
#   - name: nginx
#     path: /var/log/nginx/*.log
#     options:
#       - daily
#       - compress
#       - rotate 6
#       - missingok
#       - copytruncate
#       - delaycompress
#     scripts:
#       postrotate: "[ -s /run/nginx.pid ] && kill USR1 `cat /run/nginx.pid`"
#

# package name (version)
logrotate_package: logrotate
# script to install
logrotate_scripts: []
```


## Example playbook

```
- hosts: all
  sudo: yes
  roles:
    - franklinkim.logrotate
  vars:
    logrotate_scripts:
      - name: syslog
        path: /var/log/syslog
        options:
          - daily
          - compress
          - rotate 6
          - missingok
          - copytruncate
          - delaycompress
```

## Testing

```
$ git clone https://github.com/buluma/ansible-logrotate.git
$ cd ansible-logrotate
$ vagrant up
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) We Are Interactive under the MIT license.
