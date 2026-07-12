Extend-Disk
=========

Extends the disk of a linux lvm when there is available, unallocated disk space. Tested in Ubuntu.

Requirements
------------

This role relies on the community.general collection. There must be unallocated disk space available on the system.

Role Variables
--------------

None. The role discovers everything it needs from gathered facts:

1. Finds the device mounted at `/` and matches it to a logical volume in the LVM facts, giving `volume_group` and `logical_volume`.
2. Finds the physical volume backing that volume group (the role fails if the VG spans more than one PV, since the disk to extend would be ambiguous).
3. Derives `disk` and the partition number from the PV path (e.g. `/dev/sda3` → `/dev/sda` partition 3, `/dev/nvme0n1p3` → `/dev/nvme0n1` partition 3).

On MBR (msdos) disks where the PV is a logical partition (number 5+, the
default Debian layout), the role grows the extended container partition to the
end of the disk before growing the PV partition itself.

The root filesystem must be on LVM, and fact gathering must be enabled.

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