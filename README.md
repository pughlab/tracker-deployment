## tracker-deployment

This repository contains Ansible playbooks and files needed to manage a tracker deployment on
a remote server.

There are a number of configurations supported, as different organizations have very
different hosting environments. These include:

 * Unprivileged access, CentOS 6

### Outline architecture

The tracker is packaged as a Java web application in a `war` file. To provide a better
environment for deployment, there is a separate Jetty-based hosting package, that
includes a fully-configured Jetty that can read an XML config file from the command
line. This is a separate `jar` file.

Most of the local configuration is injected into the Jetty XML file that deploys the
tracker application.

Most of these resources are pulled from various releases on Github. This saves
building within the deployment process.


### Using the deployment system

To deploy, use something like:

With Vagrant:

    ansible-playbook -v -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory --private-key=~/.vagrant.d/insecure_private_key -u vagrant deploy.yml

On a regular server:

    ansible-playbook -v -i inventory.txt ...connection args... deploy.yml


### Notes

 * The deployment system uses a special variable `app_layout=xxx` which can be added
   to a host in the inventory file. This will include a `local_layout_xxx.yml` file
   of variables, which can override defaults appropriate to a given OS. These files are
   ignored by `git`. This allows you to set up your own layout in an inventory file,
   and manage it any way you choose.
