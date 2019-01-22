Role Name
=========

This role is designed to do a baseline configuration and prep for a newly configured Fedora system for use by Red Hat employees.  

Install this directory in your `roles` path under the name `rhfedora`

```
git clone this-git-repo roles/rhfedora
```

Requirements
------------

At this point in time DNF is the required package manager.  YUM support maybe added at a later point in time.  Additionally ansible, python, and 

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

This role is designed to be used with tags depending upon your desired end state.  Currently there are three major tags that need to be considered `baseline`, `platform`, and `developer`.  Without limiting to any tags all 3 major components will be installed with the `baseline` tasks always executing unless skipped.


### Install all profiles
```
$ ansible-playbook rhfedora.yml -K
```

### Platform Profile
```
$ ansible-playbook rhfedora.yml -t platform -K
```

### Developer Profile.
```
$ ansible-playbook rhfedora.yml -t developer -K
```

### Baseline Profile Only
```
$ ansible-playbook rhfedora.yml -t baseline -K
```

### Developer or Platform Without RH Baseline
```
$ ansible-playbook rhfedora.yml -t platform --skip-tags baseline -K
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
