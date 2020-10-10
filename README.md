# Ansible ansible-servicenow-midserver role

[![Build Status](https://img.shields.io/travis/mikevdberge/ansible-servicenow-midserver.svg)](https://travis-ci.org/github/mikevdberge/ansible-servicenow-midserver)
[![Galaxy](http://img.shields.io/badge/galaxy-mikevdberge.ansible_servicenow_midserver-blue.svg?style=flat-square)](https://galaxy.ansible.com/mikevdberge/ansible-servicenow-midserver)
[![GitHub Tags](https://img.shields.io/github/tag/mikevdberge/ansible-servicenow-midserver.svg)](https://github.com/mikevdberge/ansible-servicenow-midserver)
[![GitHub Stars](https://img.shields.io/github/stars/mikevadberge/ansible-servicenow-midserver.svg)](https://github.com/mikevdberge/ansible-servicenow-midserver.)

> `mikevdberge.ansible-servicenow-midserver` is an [Ansible](http://www.ansible.com) role which:
>
> * installs Servicenow MID server agent
> * configures ServiceNow MID server agent
> * manages ServiceNow MID server agent
> * configures mid service

## Installation

Using `ansible-galaxy`:

```shell
$ ansible-galaxy install mikevdberge.ansible-servicenow-midserver
```

Using `requirements.yml`:

```yaml
- src: mikevdberge.ansible-servicenow-midserver
```

Using `git`:

```shell
$ git clone https://github.com/mikevdberge/ansible-servicenow-midserver.git mikevdberge.ansible-servicenow-midserver
```

## Dependencies

* Ansible >= 2.0

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

| Variables | Required | Default value | Description |
|-----------|----------|---------------|-------------|
| now_instance_mid_name  | false     |           | Name of the MID Server agent |
| now_mid_base_https_uri  | true     | https://install.service-now.com/glide/distribution/builds/package/mid    | Https endpoint for package download |
| now_mid_base_http_uri  | true     | http://install.service-now.com/glide/distribution/builds/package/mid      | Https endpoint for package download |
| now_mid_base_path_win  | true     | c:/servicenow          | Base installation path on Windows|
| now_mid_base_path  | true     | /opt/servicenow          | Base installation on Linux |
| now_mid_base_user  | false     |           | User |
| now_mid_base_group  | false     |           | Group |
| mid_proxy_use_proxy  | false     | false    | User proxy |
| mid_proxy_host  | false     |     | Proxy host|
| mid_proxy_port  | false     |     | Proxy port|
| mid_proxy_username  | false     |     | Proxy user name|
| mid_proxy_password  | false     |     | Proxy user password|
| wrapper_java_maxmemory  | false     | 1024    | Maximum Java Heap Size (in MB) |



```yaml
---
# package name (version)
ansible_servicenow-midserver_package: ansible-servicenow-midserver
# service name
ansible_servicenow-midserver_service_name: ansible-servicenow-midserver
# start on boot
ansible_servicenow-midserver_service_enabled: yes
# current state: started, stopped
ansible_servicenow-midserver_service_state: started

```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

```yaml
---
- name: restart ansible-servicenow-midserver
  service:
    name: "{{ ansible_servicenow-midserver_service_name }}"
    state: restarted
  when: ansible_servicenow-midserver_service_state != 'stopped'

```

## A new section after the handler section

Lorem ipsum dolor sit atem ...

## Usage

This is an example playbook:

```yaml
---
- hosts: all
  # pre_tasks for installing dependencies for running the tests within docker
  # pre_tasks:
  #  - name: Installing openssh
  #    action: "{{ ansible_pkg_mgr }} pkg=my-package state=present"
  roles:
    - mikevdberge.ansible-servicenow-midserver
  vars:
    now_instance_mid_name: my_midserver_agent

```

## A new section after the usage section

Lorem ipsum dolor sit atem ...

## Testing

```shell
$ git clone https://github.com/mikevdberge/ansible-servicenow-midserver.git
$ cd ansible-servicenow-midserver
$ make test
```

## Contributing
In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

*Note: To update the `README.md` file please install and run `ansible-role`:*

```shell
$ gem install ansible-role
$ ansible-role docgen
```

## License
Copyright (c) QHSE Professionals under the MIT license.
