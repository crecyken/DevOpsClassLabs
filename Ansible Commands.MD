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

