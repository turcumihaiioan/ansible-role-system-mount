system_mount
=========

This role allows you to use the ansible.posix.mount module to control active and configured mount points in /etc/fstab.

Requirements
------------

ansible >= 2.10

Role Variables
--------------

```yml
system_mount:
  first_entry:
    backup: ...
    boot: ...
    dump: ...
    fstab: ...
    fstype: ...
    opts: ...
    passno: ...
    path: ...
    src: ...
    state: ...
  second_entry:
    .
    .
    .
  .
  .
  .
```

Dependencies
------------

None

Example Playbook
----------------

#### Mount and ensure a filesystem in fstab:
```yml
- hosts: servers
  vars:
    system_mount:
      sbd1:
        fstype: xfs
        path: /mnt/sdb1-mnt-pnt
        src: /dev/sdb1
        state: mounted
  roles:
    - turcumihaiioan.system_mount
```

#### Remount a filesystem in read-only:
```yml
- hosts: servers
  vars:
    system_mount:
      sbd2:
        path: /mnt/sdb2-mnt-pnt
        opts: ro
        state: remounted
  roles:
    - turcumihaiioan.system_mount
```

#### Unmount and remove a filesystem from fstab:
```yml
- hosts: servers
  vars:
    system_mount:
      sbd3:
        path: /mnt/sdb3-mnt-pnt
        state: absent
  roles:
    - turcumihaiioan.system_mount
```

License
-------

GPL-3.0-only

Author Information
------------------

Role created by Turcu Mihai Ioan
