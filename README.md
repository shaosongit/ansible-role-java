# [java](#java)

Install and configure java on your system.

|Travis|GitHub|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-java.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-java)|[![github](https://github.com/robertdebock/ansible-role-java/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-java/actions)|[![quality](https://img.shields.io/ansible/quality/22732)](https://galaxy.ansible.com/robertdebock/java)|[![downloads](https://img.shields.io/ansible/role/d/22732)](https://galaxy.ansible.com/robertdebock/java)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-java.svg)](https://github.com/robertdebock/ansible-role-java/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.java
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: Default
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for java

# Set the vendor of java, valid values are "openjdk" and "oracle".
java_vendor: openjdk

# Set the variable to install the type, valid values are "jre" and "jdk".
java_type: jre

# Set the version of java, valid values are "6", 7", "8", "9", "10", "11",
# "12" or "13".
# By default, a distibution default is used, mapped in `vars/main.yml`.
# By setting java_version, you overwrite this default to your selected
# version.
# java_version: 8

# Set the format of the installation source, valid values are "targz" and
# "rpm". This is only valid with "java_vendor == oracle"
java_format: targz

# Where do the RPMs come from when installing Oracle RPMs?
# Either "local" or "repository".
# Valid for "java_vendor == oracle" and "java_format" == "rpm"
java_rpm_source: local

# Choose if you can JCE installed. Only applicable for (both):
# - java_vendor == "oracle"
# - java_version == "8"
java_jce: yes

# In case of "java_vendor == oracle" and "java_format == targz", a directory
# as to be set where to install.
java_install_directory: /opt
```

## [Requirements](#requirements)

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

## [Status of requirements](#status-of-requirements)

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/java.png "Dependency")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|alpine|all|
|amazon|all|
|el|7, 8|
|debian|buster, bullseye|
|fedora|all|
|opensuse|all|
|ubuntu|focal, bionic, xenial|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.


## [Included version(s)](#included-versions)

This role [refers to a version](https://github.com/robertdebock/ansible-role-java/blob/master/vars/main.yml) released by Oracle. Check the released version(s) here:
- [java](https://www.oracle.com/technetwork/java/javaseproducts/downloads/index.html).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.
## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-java) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-java/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0

## [Contributors](#contributors)

I'd like to thank everybody that made contributions to this repository. It motivates me, improves the code and is just fun to collaborate.

- [it-praktyk](https://github.com/it-praktyk)

## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
