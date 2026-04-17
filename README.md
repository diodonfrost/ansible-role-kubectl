ansible-role-kubectl
=============

Ansible role for install kubectl package.

Role Variables
--------------

| Variable                  | Default                      | Description                                                                                                                        |
|---------------------------|------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| `kubectl_version`         | `"latest"`                   | Version of kubectl to install. `"latest"` resolves the current stable release via `https://dl.k8s.io/release/stable.txt`; otherwise pin a literal version (e.g. `"v1.29.0"`). |
| `kubectl_path`            | `/usr/local/bin/` (on Linux) | Directory where the `kubectl` binary is installed. Must end with a trailing slash.                                                 |
| `kubectl_checksum_verify` | `true`                       | When enabled, the downloaded binary is checked against the SHA256 published at `https://dl.k8s.io/release/<version>/bin/linux/amd64/kubectl.sha256`. Set to `false` to skip verification (e.g. air-gapped environments). |

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: diodonfrost.kubectl

Local Testing
-------------

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://libvirt.org/) (If you test a system other than Linux)
* [Vagrant](https://www.vagrantup.com/downloads.html) (If you test a system other than Linux)

Testing with Docker
-------------------

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 22.04
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create centos 7 instance
image=ansible-centos:7 molecule create

# Apply role on centos 7 instance
image=ansible-centos:7 molecule converge

# Launch tests on centos 7 instance
image=ansible-centos:7 molecule verify
```

Testing with Vagrant and Libvirt
--------------------------------

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd

# Test ansible role with Windows
molecule test -s windows
```

License
-------

Apache Software License 2.0

Author Information
------------------

This role was created in 2023 by diodonfrost.
