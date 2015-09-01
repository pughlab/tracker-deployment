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
