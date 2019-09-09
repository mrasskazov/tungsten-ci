tungsten-ci
===========

This repository contains ansible playbooks for deploy Tungsten Fabric CI local implementation.

How to run
----------
Create VM that will be used as zuul host. For example Ubuntu Bionic cloud image based.
Make sure that you can login to this VM via ssh.

Make sure that *ansible* is installed. This playbooks was tested on ansible==2.6.5

Clone the repository::

    # git clone https://github.com/mrasskazov/tungsten-ci.git && cd tungsten-ci/


Update the dependencies (git submodules)::

    # git submodule init && git submodule sync && git submodule update


Check the defaults in *zuul-vars.yml*. You can redefine then using *--extra-vars* CLI option.

Run playbook::

    # ansible-playbook -i <VM_USERNAME>@<VM_IP_OR_HOST>, --extra-vars "zuul_config_merger_git_user_name=gerrit_username zuul_config_merger_ssh_private_key_file=PATH/TO/PRIVATE_KEY_FILE" zuul.yml



(Pay attention on comma after VM_IP_OR_HOST value)

During the run you should specify username and password for accessing Openstack clouds. They using for
creating builder instances by nodepool.

After playbook will be completed you may access Zuul web UI via::

    http://<VM_IP_OR_HOST>:9000
