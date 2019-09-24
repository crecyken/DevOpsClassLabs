# Your first commands

Now that you’ve installed Ansible, it’s time to get started with some basics.

Edit (or create) /etc/ansible/hosts and put one or more remote systems in it. Your public SSH key should be located in authorized_keys on those systems:

```sh
localhost
192.168.10.20
myhost.mydomain.com
```
We’ll assume you are using SSH keys for authentication. To set up SSH agent to avoid retyping passwords, you can do:
```sh
ssh-keygen
ssh-copyid user@<serverIp>
```

Now ping all your nodes:

```sh
ansible all -m ping
```

# Introduction To Ad-Hoc Commands

What’s an ad-hoc command?

An ad-hoc command is something that you might type in to do something really quick, but don’t want to save for later.

## Parallelism and Shell Commands

## AD-HOC Syntax
```sh
ansible <pattern_goes_here> -m <module_name> -a <arguments>
```

Now to run the command on all servers in a group, in this case, web, in 10 parallel forks:

```sh
$ ansible web -a "/sbin/reboot" -f 10
```
The *-f 10* in the above specifies the usage of 10 simultaneous processes to use. You can also set this in Configuring Ansible to avoid setting it again. The default is actually 5, which is really small and conservative

Using the shell module looks like this:
```sh
$ ansible web -m shell -a 'echo $TERM'
```

## File Transfer

To transfer a file directly to many servers:
```sh
$ ansible atlanta -m copy -a "src=/etc/hosts dest=/tmp/hosts"
```

The file module allows changing ownership and permissions on files. These same options can be passed directly to the copy module as well:

```sh
$ ansible webservers -m file -a "dest=/srv/foo/a.txt mode=600"
$ ansible webservers -m file -a "dest=/srv/foo/b.txt mode=600 owner=mdehaan group=mdehaan"
```

The file module can also create directories, similar to mkdir -p:
```sh
$ ansible webservers -m file -a "dest=/path/to/c mode=755 owner=mdehaan group=mdehaan state=directory"
```

As well as delete directories (recursively) and delete files:
```sh
$ ansible webservers -m file -a "dest=/path/to/c state=absent"
```

## Managing Packages

There are modules available for yum and apt. Here are some examples with yum.

Ensure a package is installed, but don’t update it:
```sh
$ ansible webservers -m yum -a "name=telnet state=present"
```

Ensure a package is installed to a specific version:
```sh
$ ansible webservers -m yum -a "name=acme-1.5 state=present"
```
Ensure a package is at the latest version:
```sh
$ ansible webservers -m yum -a "name=telnet state=latest"
```
Ensure a package is not installed:
```sh
$ ansible webservers -m yum -a "name=telnet state=absent"
```

## Users and Groups
The ‘user’ module allows easy creation and manipulation of existing user accounts, as well as removal of user accounts that may exist:
```sh
$ ansible all -m user -a "name=foo password=<crypted password here>"

$ ansible all -m user -a "name=foo state=absent"
```

## Managing Services
Ensure a service is started on all webservers:
```sh
$ ansible webservers -m service -a "name=httpd state=started"
```
Alternatively, restart a service on all webservers:
```sh
$ ansible webservers -m service -a "name=httpd state=restarted"
```

Ensure a service is stopped:
```sh
$ ansible webservers -m service -a "name=httpd state=stopped"
```

## Gathering Facts

Facts are described in the playbooks section and represent discovered variables about a system.

```sh
$ ansible all -m setup
```

