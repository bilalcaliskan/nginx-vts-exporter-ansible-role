## Node Exporter Ansible Role

[![CI](https://github.com/bilalcaliskan/nginx_vts_exporter-ansible-role/workflows/CI/badge.svg?event=push)](https://github.com/bilalcaliskan/nginx_vts_exporter-ansible-role/actions?query=workflow%3ACI)

Installs and configures nginx_vts_exporter to expose Nginx metrics to Prometheus on RHEL/CentOS 7/8 instances.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: true`, or invoke the role in your playbook like:

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.nginx_vts_exporter
```

### Role Variables
See the default values in [defaults/main.yml](defaults/main.yml). You can overwrite them in [vars/main.yml](vars/main.yml) if neccessary or you can set them while running playbook.

> Please note that this role will ensure that `firewalld` systemd service on your servers are started and enabled by default. If you want to stop and disable `firewalld` service, please modify below variable as false when running playbook:  
> ```yaml  
> firewalld_enabled: false

## Dependencies

None

### Example Playbook File For Installation

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.nginx_vts_exporter
      vars:
        nginx_host: localhost
        image_url: sophos/nginx-vts-exporter:latest
        auth_required: false
        registry: docker.io
```

### License

MIT / BSD
