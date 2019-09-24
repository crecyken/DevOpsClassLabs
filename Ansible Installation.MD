# Basics / What Will Be Installed

Ansible by default manages machines over the SSH protocol.

Once Ansible is installed, it will not add a database, and there will be no daemons to start or keep running.You only need to install it on one machine (which could easily be a laptop) and it can manage an entire fleet of remote machines from that central point.

# Control Node Requirements

Currently Ansible can be run from any machine with Python 2 (version 2.7) or Python 3 (versions 3.5 and higher) installed. Windows isn’t supported for the control node.

# Managed Node Requirements

On the managed nodes, you need a way to communicate, which is normally ssh. By default this uses sftp. If that’s not available, you can switch to scp in ansible.cfg. You also need Python 2 (version 2.6 or later) or Python 3 (version 3.5 or later).

# Installing the Control Node

On RHEL and CentOS:
```sh
$ sudo yum install ansible
```
