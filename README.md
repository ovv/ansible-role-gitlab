ovv.gitlab
==========

Ansible role to install and configure [Gitlab](https://about.gitlab.com)

Installation
------------

To install this roles clone it into your roles directory.

```bash
$ git clone https://github.com/ovv/ansible-role-gitlab.git ovv.gitlab
```

If your playbook already reside inside a git repository you can clone it by using git submodules.

```bash
$ git submodule add -b master https://github.com/ovv/ansible-role-gitlab.git ovv.gitlab
```

Role Variables
--------------

* gitlab_url: Gitlab access URL.
* gitlab_config_template: Gitlab configuration template (default to `etc/gitlab/gitlab.rb.j2`).

* gitlab_unicorn_worker_processes: Number of worker process (default to `2`).
* gitlab_unicorn_worker_timeout: Worker process timeout (default to `60`).

* gitlab_letsencrypt: Setup letsencrypt certificates (default to `False`).
* gitlab_letsencrypt_contacts: List of contact email for letsencrypt
* gitlab_ssl_certificate: Custom certificates to be used
    cert: Certificate fullchain
    key: Certificate key

* gitlab_email: Send email as.
* gitlab_noreply_email: Reply-To email adress

* gitlab_skip_sysctl_setup: Skip setting up sysctl values (default to `False`).
* gitlab_dpkg_unsafe_io: Use `--force-unsafe-io` option for dpkg (default to `False`).

* gitlab_registry: 
    url: gitlab registry url
    nginx: Custom value for the registry nginx
      key: value

* gitlab_pages: 
    url: gitlab pages url
    nginx: Custom value for the pages nginx
      key: value

* gitlab_smtp:
    address: SMTP server address
    port: SMTP server port
    user: username
    password: password
    domain: domain
    auth: SMTP authentification type
    starttls: Enable starttls (default to `true`)
    tls: Enable tls (default to `false`)

Example Playbook
----------------

```yml
- hosts: gitlab
  tags:
    - gitlab
  roles:
    - ovv.gitlab
  vars:
    gitlab_url: https://git.example.com
    gitlab_letsencrypt: True
    gitlab_email: gitlab@example.com
    gitlab_unicorn_worker_processes: 4
```

License
-------

MIT
