<p><img src="http://www.timtyson.us/wordpress/wp-content/uploads/2014/05/database-mysql-logo-572x572.png" alt="database logo" title="database" align="right" height="60" /></p>

# Ansible Role: mysqld exporter

[![Build Status](https://travis-ci.com/cloudalchemy/ansible-mysqld_exporter.svg?branch=master)](https://travis-ci.com/cloudalchemy/ansible-mysqld_exporter)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/badge/ansible%20role-cloudalchemy.mysqld_exporter-blue.svg)](https://galaxy.ansible.com/cloudalchemy/mysqld_exporter/)
[![GitHub tag](https://img.shields.io/github/tag/cloudalchemy/ansible-mysqld_exporter.svg)](https://github.com/cloudalchemy/ansible-mysqld_exporter/tags)

## Description

Deploy prometheus [mysqld exporter](https://github.com/prometheus/mysqld_exporter) using ansible.

## Requirements

- Ansible >= 2.7 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `mysqld_exporter_version` | 0.12.1 | mysqld exporter package version. Versions before 0.11 aren't supported. |
| `mysqld_exporter_binary_local_dir` | "" | Allows to use local packages instead of ones distributed on github. As parameter it takes a directory where `mysqld_exporter` binary is stored on host on which ansible is ran. This overrides `mysqld_exporter_version` parameter |
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

The preferred way of locally testing the role is to use Docker and [molecule](https://github.com/ansible-community/molecule) (v3.x). You will have to install Docker on your system. See "Get started" for a Docker package suitable to for your system. Running your tests is as simple as executing `molecule test`.

## Continuous Integration

Combining molecule and circle CI allows us to test how new PRs will behave when used with multiple ansible versions and multiple operating systems. This also allows use to create test scenarios for different role configurations. As a result we have a quite large test matrix which can take more time than local testing, so please be patient.

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## Troubleshooting

See [troubleshooting](TROUBLESHOOTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
