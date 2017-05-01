nvm
========

Install nvm and Node.js.

Requirements
------------

git, curl, build-essential, libssl-dev. Requirements are installed by the role.

Role Variables
--------------

* `nvm_version` nvm version tag, or `HEAD`.
* `nvm_node_version` Node.js version.
* `nvm_install_path` nvm folder path. Defaults to `~/.nvm`.

Version default values can be found in `defaults/main.yml`.

Dependencies
------------

No dependencies.

Example Playbook
-------------------------

    - hosts: servers
      roles:
        - role: drunomics.nvm
          nvm_version: 0.33.2
          nvm_node_version: 6.10.*
          
Usage
-----
For npm and node executables to be found, nvm needs to alter the PATH. The role
does so by altering ~/.bashrc. If system-wide installation is enabled, the 
global bashrc and /etc/environment is adapted.

However, ansible does not always pick the changed PATH variable up; e.g. when
using the docker connection plugin. To make use of npm in ansible, the PATH
variable must be adjusted accordingly. The role provides the fact `nvm_bin_dir`
such that it can be done as follows:

```
  shell: echo "This works with every task."
  environment:
    PATH: "{{ nvm_bin_dir }}:{{ ansible_env.PATH }}"
```

License
-------

BSD

Credits
------------------
This is role forked from Jarno Keskikangas (https://github.com/leonidas/ansible-nvm)
and https://github.com/stephdewit/ansible-nvm.
