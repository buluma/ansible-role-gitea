# [gitea](#gitea)

Install and configure gitea on your system.

|GitHub|GitLab|Quality|Downloads|Version|Issues|Pull Requests|
|------|------|-------|---------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-gitea/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-gitea/actions)|[![gitlab](https://gitlab.com/buluma/ansible-role-gitea/badges/master/pipeline.svg)](https://gitlab.com/buluma/ansible-role-gitea)|[![quality](https://img.shields.io/ansible/quality/59670)](https://galaxy.ansible.com/buluma/gitea)|[![downloads](https://img.shields.io/ansible/role/d/59670)](https://galaxy.ansible.com/buluma/gitea)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-gitea.svg)](https://github.com/buluma/ansible-role-gitea/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-gitea.svg)](https://github.com/buluma/ansible-role-gitea/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-gitea.svg)](https://github.com/buluma/ansible-role-gitea/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.gitea
```

The machine needs to be prepared. In CI this is done using `molecule/default/prepare.yml`:
```yaml
---
- name: prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
```


## [Role Variables](#role-variables)

The default values for the variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for gitea

gitea_version: "1.17.0"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-gitea/blob/main/requirements.txt).

## [Status of used roles](#status-of-requirements)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/buluma/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-gitea/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|amazon|Candidate|
|debian|bullseye|
|el|all|
|fedora|all|
|opensuse|all|

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
