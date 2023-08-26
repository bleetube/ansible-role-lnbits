# Ansible Role: lnbits

This Ansible Role installs [lnbits](https://github.com/lnbits/lnbits). It is intended to be composed with a separate role for the web proxy configuration.

Tested on:
* Ubuntu 22.04
* ~~Archlinux~~ Looks like Arch currently requires [conda](https://aur.archlinux.org/packages/miniconda3) to avoid library problems w/ python3.11

## Requirements

None.

## Dependencies

* [nginx_conf](docs/examples/nginx_conf.yml) (optional)

## Role Variables

See the role [defaults](defaults/main.yml). For a working example, see this [homelab stack](https://github.com/bleetube/satstack).

## Example Playbook

```yaml
- hosts: lnbits
  roles:
    - role: nginxinc.nginx_core.nginx
      become: yes
    - role: bleetube.lnbits
      tags: lnbits
  tasks:
    - import_tasks: nginx_conf.yml
      become: yes
```
