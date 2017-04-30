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

License
-------

BSD

Credits
------------------
This is role forked from Jarno Keskikangas (https://github.com/leonidas/ansible-nvm)
and https://github.com/stephdewit/ansible-nvm.
