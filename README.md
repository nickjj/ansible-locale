## What is ansible-locale? [![Build Status](https://secure.travis-ci.org/nickjj/ansible-locale.png)](http://travis-ci.org/nickjj/ansible-locale)

It is an [ansible](http://www.ansible.com/home) role to install the locales package and set your system's locale.

### What problem does it solve and why is it useful?

It is a good idea to use a consistent locale across your servers and certain services like postgres will not install to the expected path if the locale is not configured.

## Role variables

```
---
# Which locale(s) should be used?
# The state can be present or absent.
locale_locales:
  - { locale: en_US.UTF-8, state: present }

# The amount in seconds to cache apt-update.
apt_cache_valid_time: 86400
```

## Example playbook

For the sake of this example let's say you have a group called **app** and you have a typical `site.yml` file.

To use this role edit your `site.yml` file to look something like this:

```
---
- name: ensure apps is configured
- hosts: app

  roles:
    - { role: nickjj.locale, tags: locale }
```

Let's say you want to edit the locale, you can do this by opening or creating `group_vars/app.yml` which is located relative to your `inventory` directory and then making it look something like this:

```
---
locale_locales:
  - { locale: de_DE.UTF-8, state: present }

```

## Installation

`$ ansible-galaxy install nickjj.locale`

## Requirements

Tested on ubuntu 12.04 LTS but it should work on other versions that are similar.

## License

MIT