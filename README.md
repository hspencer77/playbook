playbook
========

This is a playbook for deploying Eucalyptus via packages in accordance with reference Architectures. Depends on ansible 1.3 or above.

The first playbook "dev-test-large" aims to deploy Eucalyptus in a distributed setup per the reference architecture found here:

http://www.eucalyptus.com/eucalyptus-cloud/reference-architectures/dev-test-large  (minus SAN).

All of these playbooks assume you have an inventory file configured.  Regarding NC's and networking mode, this playbook will create a bridge on a specific interface. It assumes you have an ansible inventory file which looks like this:

[clc]
<myclcip>

[walrus]
<mywalrusip>

[cc]
<myclusterip>

[sc]
<mystorageip>

[nc]
<mync1>
<mync2>

You would then run the playbook with (for example):

# ansible-playbook -i dev-test-large-hosts site.yml -u root -k

Add additional options for sudo, ssh key etc. as required.

** PLAYBOOK CONFIG **

Note that variables for the installation should be configured in vars/main.yml.  Here you can change the software version, network settings etc.

** ANSIBLE CONFIGURATION **

I've not yet removed all of the deprecated variable definitions, you might want to set this parameter in /etc/ansible/ansible.cfg to remove warnings:

deprecation_warnings=False

You will definately need this too, for now:

error_on_undefined_vars = False
