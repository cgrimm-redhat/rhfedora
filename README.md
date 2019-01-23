Role Name
=========

This role is designed to do a baseline configuration and prep for a newly configured Fedora system for use by Red Hat employees.  

Install this directory in your `roles` path under the name `rhfedora`

```
git clone this-git-repo roles/rhfedora
```

Requirements
------------

At this point in time DNF is the required package manager.  YUM support maybe added at a later point in time.  Additionally ansible, python, and libselinux-python 

```
$ sudo dnf install ansible python libselinux-python
```

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Usage
------------

This role is designed to be used with tags depending upon your desired end state.  Currently there are two major profiles split apart via tags `baseline` and  `developer`.  The baseline package will install a subset of applications along with a base configuration for using your Fedora system with the RH networks.  This will include items such as inteagrtion of kerberos, VPN, etc.  The developer profile is an additional set of applications & configurations that will allow for app development, docker usage, etc to be built into the system for use.  Without limiting any tags both profiles will be installed. Below are some tagged use cases.


### Install both profiles
```
$ ansible-playbook rhfedora.yml -K
```

### Install Baseline Profile Only
```
$ ansible-playbook rhfedora.yml --skip-tags developer -K
```

## Example Playbook

```
---
- hosts: localhost
  become: true
  roles:
    - rhfedora
```

License
-------

BSD

Author Information
------------------
Chris Grimm - cgrimm@redhat.com - github.com/cgrimm-redhat
