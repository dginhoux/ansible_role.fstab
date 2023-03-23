# ROLE dginhoux.fstab



## DESCRIPTION

This role configure linux mounts and generate `/etc/fstab`.



## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip node with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36, 37 |
| EL | 7, 8 |

#### ANSIBLE VERSION

Ansible >= 2.12

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.fstab
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.fstab dginhoux.fstab
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.fstab
      ansible.builtin.include_role:
        name: dginhoux.fstab
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

```yaml
fstab_configure: true

fstab_reload: true
fstab_create_additional_dirs: true

fstab_tmpfs: false
fstab_tmpfs_options:
  - nodev
  - nosuid
  - noatime

fstab_sysfs: true
fstab_sysfs_options:
  - defaults
  - noatime

fstab_proc: true
fstab_proc_options:
  - defaults
  - noatime

fstab_mounts:
  - source: /dev/sda1
    target: /boot
    type: ext2
    options:
      - defaults
      - noatime
    dump: false
    fsck: 1

  - source: /dev/mapper/vg0-lv--root
    target: /
    type: xfs
    options:
      - defaults
      - noatime
    dump: false
    fsck: 1

  - source: /dev/mapper/vg0-lv--home
    target: /home
    type: xfs
    options:
      - defaults
      - noatime
    dump: false
    fsck: 1

  - source: /dev/mapper/vg0-lv--opt
    target: /opt
    type: xfs
    options:
      - defaults
      - noatime
    dump: false
    fsck: 1

  - source: /dev/mapper/vg0-lv--tmp
    target: /tmp
    type: xfs
    options:
      - defaults
      - noatime
    dump: false
    fsck: 0

  - source: /dev/mapper/vg0-lv--usr
    target: /usr
    type: xfs
    options:
      - defaults
      - noatime
    dump: false
    fsck: 1

  - source: /dev/mapper/vg0-lv--var
    target: /var
    type: xfs
    options:
      - defaults
      - noatime
    dump: false
    fsck: 1

  - source: /dev/mapper/vg0-lv--swap
    target: none
    type: swap
    options:
      - sw
    dump: false
    fsck: 0
```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
