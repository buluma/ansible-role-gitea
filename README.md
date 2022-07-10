# [gitea](#gitea)

Install and configure Gitea on your systems.

|GitHub|GitLab|Quality|Downloads|Version|Issues|Pull Requests|
|------|------|-------|---------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-gitea/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-gitea/actions)|[![gitlab](https://gitlab.com/buluma/ansible-role-gitea/badges/master/pipeline.svg)](https://gitlab.com/buluma/ansible-role-gitea)|[![quality](https://img.shields.io/ansible/quality/59670)](https://galaxy.ansible.com/buluma/gitea)|[![downloads](https://img.shields.io/ansible/role/d/59670)](https://galaxy.ansible.com/buluma/gitea)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-gitea.svg)](https://github.com/buluma/ansible-role-gitea/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-gitea.svg)](https://github.com/buluma/ansible-role-gitea/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-gitea.svg)](https://github.com/buluma/ansible-role-gitea/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: true
  roles:
    - buluma.gitea
  vars:
    gitea_http_domain: localhost
    gitea_root_url: http://localhost
```

The machine needs to be prepared. In CI this is done using `molecule/default/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  become: true
  tasks:
    - name: install dependencies for gitea (RedHat based systems)
      yum:
        name: "{{ redhat_packages }}"
        state: present
        update_cache: true
      when: ansible_os_family == "RedHat"
    - name: install dependencies for gitea (Debian based systems)
      apt:
        name: "{{ debian_packages }}"
        state: present
        update_cache: true
      when: ansible_os_family == "Debian"

  vars:
    debian_packages:
      - git
      - curl
      - xz-utils
    redhat_packages:
      - git
      - curl
      - xz
```


## [Role Variables](#role-variables)

The default values for the variables are set in `defaults/main.yml`:
```yaml
---
gitea_version: "1.13.7"
gitea_version_check: true
gitea_dl_url: "https://github.com/go-gitea/gitea/releases/download/v{{ gitea_version }}/gitea-{{ gitea_version }}-linux-{{ gitea_arch }}"
gitea_gpg_key: "7C9E68152594688862D62AF62D9AE806EC1592E2"
gitea_gpg_server: "hkps://keys.openpgp.org"

gitea_app_name: "Gitea"
gitea_user: "gitea"
gitea_group: "gitea"
gitea_home: "/var/lib/gitea"
gitea_shell: "/bin/false"
gitea_systemd_cap_net_bind_service: false

gitea_repository_root: "{{ gitea_home }}"
gitea_user_repo_limit: -1

gitea_http_domain: localhost
gitea_root_url: http://localhost:3000
gitea_protocol: http
gitea_http_listen: 127.0.0.1
gitea_http_port: 3000
gitea_disable_http_git: false
gitea_offline_mode: true

gitea_lfs_server_enabled: false
gitea_lfs_content_path: "{{ gitea_home }}/data/lfs"
gitea_lfs_jwt_secret: ''
# gitea_lfs_content_path: "data/lfs"
gitea_lfs_secret: SomethingVeryLong
gitea_lfs_mode: true

gitea_db_type: sqlite3
gitea_db_host: 127.0.0.0:3306
gitea_db_name: root
gitea_db_user: gitea
gitea_db_password: lel
gitea_db_ssl: disable
gitea_db_path: "{{ gitea_home }}/data/gitea.db"

gitea_ssh_listen: 0.0.0.0
gitea_ssh_domain: localhost
gitea_start_ssh: true
gitea_ssh_port: 2222

gitea_secret_key: T0pS3cr31
gitea_internal_token: SomethingVeryLong
gitea_disable_git_hooks: true

gitea_show_user_email: false
gitea_disable_gravatar: true
gitea_disable_registration: false
gitea_show_registration_button: true
gitea_require_signin: true
gitea_enable_captcha: true
gitea_only_allow_external_registration: false
gitea_enable_notify_mail: false
gitea_mail_default: onmention
gitea_autowatch_new_repo: false
gitea_autowatch_on_change: true
gitea_show_mailstones_dashboard: true

gitea_force_private: false

gitea_mailer_enabled: false
gitea_mailer_skip_verify: false
gitea_mailer_tls_enabled: true
gitea_mailer_host: localhost:25
gitea_mailer_from: noreply@your.domain
gitea_mailer_user: ""
gitea_mailer_password: ""
gitea_mailer_type: smtp

gitea_fail2ban_enabled: false
gitea_fail2ban_jail_maxretry: 10
gitea_fail2ban_jail_findtime: 3600
gitea_fail2ban_jail_bantime: 900
gitea_fail2ban_jail_action: iptables-allports

gitea_oauth2_enabled: true
gitea_oauth2_jwt_secret: ''

gitea_metrics_enabled: false
gitea_metrics_token: ~

gitea_themes: gitea,arc-green
gitea_theme_default: gitea

gitea_repo_indexer_enabled: false
gitea_repo_indexer_include: ""
gitea_repo_indexer_exclude: ""
gitea_repo_exclude_vendored: true
gitea_repo_indexer_max_file_size: 1048576

gitea_log_level: Info

gitea_extra_config: ""

gitea_backup_on_upgrade: false
gitea_backup_location: "{{ gitea_home }}/backups/"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-gitea/blob/main/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-gitea/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|debian|all|
|ubuntu|all|
|el|7, 8|
|fedora|35|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.



If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-gitea/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-gitea/blob/master/CHANGELOG.md)

## [License](#license)

Apache-2.0

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)
