blockmounts
=========

Ansible role to configure mount points.

Requirements
------------

None.

Role Variables
--------------

A set of hashes that will mount block devices. Variables are not required. However you must specify complete sets. If nothing is specified nothing will be done.

Hash values:
 - name: the location to mount the disk at
 - src: UUID of device or path to block device
 - fstype: filesystem type
 - passno: filesystem check pass (see man fstab)
 - state: what you want to do with the mount (see ansible mount module)

Dependencies
------------

None.

Example Playbook
----------------

Set per host variables.
    #./host_vars/batman.yml:
    ---
    blockdevices_mounts:
      - name: /mnt/point
        src: UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
        fstype: ext4
        passno: 2
        state: mounted
      - name: /mnt/other_point
        src: /dev/sdb
        fstype: ext4
        passno: 2
        state: mounted

Include the role in a play.
    #./play.yml:
    ---
    - hosts: batman
      roles:
         - blockdevices

License
-------

GPLv3

Author Information
------------------

Yevgeniy Kuksenko
