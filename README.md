<p><img src="https://azure.microsoft.com/svghandler/sql-database?width=45&height=60" alt="database logo" title="database" align="right" height="60" /></p>

# Ansible Role: mysqld exporter

[![Build Status](https://travis-ci.com/cloudalchemy/ansible-mysqld-exporter.svg?branch=master)](https://travis-ci.com/cloudalchemy/ansible-mysqld-exporter)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/badge/ansible%20role-cloudalchemy.mysqld_exporter-blue.svg)](https://galaxy.ansible.com/cloudalchemy/mysqld-exporter/)
[![GitHub tag](https://img.shields.io/github/tag/cloudalchemy/ansible-mysqld-exporter.svg)](https://github.com/cloudalchemy/ansible-mysqld-exporter/tags)
[![IRC](https://img.shields.io/badge/irc.freemysqld.net-%23cloudalchemy-yellow.svg)](https://kiwiirc.com/nextclient/#ircs://irc.freemysqld.net/#cloudalchemy)

## Description

Deploy prometheus [mysqld exporter](https://github.com/prometheus/mysqld_exporter) using ansible.

## Requirements

- Ansible >= 2.6 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `mysqld_exporter_version` | 0.12.1 | mysqld exporter package version. Versions before 0.11 aren't supported. |
| `mysqld_exporter_web_listen_address` | "0.0.0.0:9104" | Address on which mysqld exporter will listen |

## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  become: yes
  roles:
    - cloudalchemy.mysqld_exporter
```

### Demo site

We provide demo site for full monitoring solution based on prometheus and grafana. Repository with code and links to running instances is [available on github](https://github.com/cloudalchemy/demo-site) and site is hosted on [DigitalOcean](https://digitalocean.com).

## Local Testing

The preferred way of locally testing the role is to use Docker and [molecule](https://github.com/metacloud/molecule) (v2.x). You will have to install Docker on your system. See "Get started" for a Docker package suitable to for your system.
We are using tox to simplify process of testing on multiple ansible versions. To install tox execute:
```sh
pip3 install tox
```
To run tests on all ansible versions (WARNING: this can take some time)
```sh
tox
```
To run a custom molecule command on custom environment with only default test scenario:
```sh
tox -e py35-ansible28 -- molecule test -s default
```
For more information about molecule go to their [docs](http://molecule.readthedocs.io/en/latest/).

If you would like to run tests on remote docker host just specify `DOCKER_HOST` variable before running tox tests.

## Travis CI

Combining molecule and travis CI allows us to test how new PRs will behave when used with multiple ansible versions and multiple operating systems. This also allows use to create test scenarios for different role configurations. As a result we have a quite large test matrix which will take more time than local testing, so please be patient.

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
