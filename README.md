# Grist Ansible role

This role installs Grist via Docker compose.

## Requirements

None

## Role Variables

All variables are listed below (see also `defaults/main.yml`).

```yml
## General
grist_hide_ui_elements:
grist_page_title_suffix: _blank
grist_single_org:
grist_widgets_list_url: https://github.com/gristlabs/grist-widget/releases/download/latest/manifest.json
grist_custom_css:
grist_force_login: "false"

grist_docker_image: gristlabs/grist
grist_docker_version: latest

grist_http_port: 8484
grist_app_home_url: "http://localhost:{{ grist_http_port }}"


# grist paths
grist_root_path: /var/local/conf
grist_config_path: "{{ grist_root_path }}/grist"
grist_persist_path: "{{ grist_root_path }}/grist"
grist_skeleton_paths:
  - "{{ grist_config_path }}"
  - "{{ grist_persist_path }}"
```

Their descriptions are as follows:

- `grist_hide_ui_elements` - See [here](https://support.getgrist.com/self-managed/#customization) for more details
- `grist_page_title_suffix` - See [here](https://support.getgrist.com/self-managed/#customization) for more details
- `grist_single_org` - Use this if you use a single organisation
- `grist_widgets_list_url` - location for downloadable grist widgets. Defaults to [grist repo](https://github.com/gristlabs/grist-widget/releases/download/latest/manifest.json)
- `grist_custom_css` - Add custom CSS (see [here](https://support.getgrist.com/self-managed/#customization) for documentation)

- `grist_force_login` - Allows grist to login if true. Default to **false**

- `grist_docker_image` - The Docekr image to use. Defaults to **gristlabs/grist**
- `grist_docker_version` - Docker image version to use. Defaults to **latest**

- `grist_http_port` - Exposed port for access. Deafults to **8484**
- `grist_app_home_url` - The named URL for the app (if you use a reverse proxy). Defaults to **http://localhost:{{ grist_http_port }}**
- `grist_root_path` - Root path for volumes. Defaults to **/var/local/conf**
- `grist_config_path` - Location of the configuration file (docker-compose). DEfaults to **{{ grist_root_path }}/grist**
- `grist_persist_path` - Persistence volume. Defaults to **{{ grist_root_path }}/grist**
- `grist_skeleton_paths` - Internal helper to create directories automatically. Drfaults to the list of volumes **[{{grist_skeleton_paths}}, {{grist_persist_path}}]**

## Dependencies

You need a machine with docker and docker-compose installed.

## Example Playbook

```yml
- hosts: servers
  roles:
      - 'laurivan.Grist'
```

## License

This project is licensed under the [MIT](https://opensource.org/licenses/MIT) license - see the [LICENSE](LICENSE) file for details.

![MIT License](https://img.shields.io/badge/license-MIT%20License-brightgreen)

## Author Information

This role was created in 2023 by [Laur Ivan](https://www.laurivan.com).

## Built With

![Ansible](https://img.shields.io/badge/ansible-5.2.0-green.svg)
![Molecule](https://img.shields.io/badge/molecule-3.4.0-green.svg)
![Goss](https://img.shields.io/badge/goss-0.3.16-green.svg)

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.
