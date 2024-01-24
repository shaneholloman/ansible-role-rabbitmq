# Ansible Role: `rabbitmq`

[![CI](https://github.com/shaneholloman/ansible-role-rabbitmq/actions/workflows/ci.yml/badge.svg)](https://github.com/shaneholloman/ansible-role-rabbitmq/actions/workflows/ci.yml)

Installs RabbitMQ on Ubuntu. EL on the way ...

## Requirements

> [!NOTE] Debian only at this time

(Red Hat / CentOS only) Requires the EPEL repository, which can be installed with the `shaneholloman.epel` role.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yml
rabbitmq_daemon: rabbitmq-server
rabbitmq_state: started
rabbitmq_enabled: true
```

Controls the RabbitMQ daemon's state and whether it starts at boot.

```yml
# temporarily not used: rabbitmq_version: "3.9.13"
```

The RabbitMQ version to install.

```yml
rabbitmq_rpm: "rabbitmq-server-{{ rabbitmq_version }}-1.el{{ ansible_distribution_major_version }}.noarch.rpm"
rabbitmq_rpm_url: "https://packagecloud.io/rabbitmq/rabbitmq-server/packages/el/{{ ansible_distribution_major_version }}/{{ rabbitmq_rpm }}/download"
```

(RedHat/CentOS only) Controls the .rpm to install.

```yml
rabbitmq_deb: "rabbitmq-server_{{ rabbitmq_version }}-1_all.deb"
rabbitmq_deb_url: "https://packagecloud.io/rabbitmq/rabbitmq-server/packages/{{ ansible_distribution | lower }}/{{ ansible_distribution_release }}/{{ rabbitmq_deb }}/download"
```

(Debian/Ubuntu only) Controls the .deb to install.

## Dependencies

None.

## Example Playbook

```yml
- hosts: rabbitmq
  roles:
    - name: shaneholloman.epel
      when: ansible_os_family == 'RedHat'
    - shaneholloman.rabbitmq
```

## License

Unlicense

## Author Information

This role was created in 2023
