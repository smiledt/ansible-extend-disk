Extend-Disk
=========

Extends the disk of a linux lvm when there is available, unallocated disk space. Tested in Ubuntu.

Requirements
------------

This role relies on the community.general collection. There must be unallocated disk space available on the system.

Role Variables
--------------

Role variables and their defaults are listed below.

    disk: /dev/sda

The disk to be extended.

    volume_group: ubuntu-vg

The volume group to be extended over the new disk space.

    logical_volume: ubuntu-lv

The logical volume to be extended.

Example Playbook
----------------

    - name: Extend the disk to all available space.
      hosts: all
      become: true
      roles:
        - extend-disk
License
-------

BSD

Author Information
------------------

Derek Smiley - Homelabber, Network Analyst, aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/

Some or much of this may have been created using snippets from other public repositories on github, reddit, or stackoverflow. I claim ownership of none of this code.