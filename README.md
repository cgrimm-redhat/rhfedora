Role Name
=========

This role is designed to do a baseline configuration and prep for a newly configured Fedora system for use by Red Hat employees.  

Install this directory in your `roles` path under the name `rhfedora`

```
git clone this-git-repo roles/rhfedora
```

Requirements
------------

At this point in time DNF is the required package manager.  YUM support maybe added at a later point in time.  Additionally ansible, python, and libselinux-python need to be installed prior to running this role against a new system. 

```
$ sudo dnf install ansible python libselinux-python
```

Role Variables
--------------

#### rh_kerberosid: 
This is simply your Red Hat userid to ensure that SSSD/Kerberos is configured properly.

#### baseline_packages:
A listing of all packages to be installed via DNF, this list must also include packages that have had custom repos created for them so that they can be installed.  It is suspected this is unlikely modification but something to be prepared for.

#### vpn_packages:
This simply provides a listing of the two Red hat RPMs for install.  These RPMs are included in the files directory of the role.

#### rpmfusion:
This simply provides a listing of the two rpmfusion urls for install of rpmfusion.

#### developer_packages:
This is a list of DNF packages that are installed for the developer profile

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
