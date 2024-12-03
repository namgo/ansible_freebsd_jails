# Ansible Collection - namgo.freebsd_jails

At present, `namgo.freebsd_jails` is a transcription of [FreeBSD Handbook - Jails](https://docs.freebsd.org/en/books/handbook/jails/) with no support for thin jails.

## Right now it does very little

- enables jails service
- initializes a ZFS store for jails
- installs a FreeBSD release into jail containers of your choosing

Currently the configuration of the jails with `jails.conf.d` is not templated or handled properly.

## Variables
Is it possible to have collection-wide `defaults`? Due to reuse of certain variables I did not want to scope them at the `role` level.

In lieu of defaults, you **MUST** define the following variables in your playbook scope:

```
jails_names: [] # jails to define
jails_nameserver: 8.8.8.8 # a dns server
jails_interface: em0 # currently unused
jails_zfs_store_root: zroot # name of zfs store where "jails" will be appended to
jails_mountpoint: /usr/local/jails # where jails zfs store will be mounted
jails_freebsd_release: 14.1 # freebsd release to install into jail
```


## Future goals
- thin jail support
- jails.conf.d entry templating of some sort
- other things I realize I'm missing

This isn't intended to be a very full-featured jails management system.

My own needs are for a minimal set of centrally-defined long-lasting jails.

Eventually I'll plop this into the Ansible Galaxy when it's more stable.
