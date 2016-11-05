# Virt dir storage pool

Create a libvirt storage pool of type `dir` backed by a logical volume. A logical volume with a given size and name will be created as well as a mountpoint and a ext4 filesystem on it.

## Requirements

Make sure, you have set up a volume-group to use with this role. A working installation of libvirtd is required as well. The libraries needed by the module `virt_pool`, which is used internally are installed by this role.

## Role Variables

Name of the lv which will be created:
```
virt_dir_storage_pool_lv: staging_vms
```

Volumegroup which will be used to create the pool:
```
virt_dir_storage_pool_vg: vg1
```

Size of the pool which will be created:
```
virt_dir_storage_pool_size: 20G
```

## Example Playbook

This example will result in a logical volume named `staging_vms`, a mount point `/mnt/vg1_staging_vms` and a storage pool named `vg1_staging_vms`.

```
- hosts: localhost
  connection: local
  become: true
  roles:
    - role: virt_dir_storage_pool
      virt_dir_storage_pool_lv: staging_vms
      virt_dir_storage_pool_vg: vg1
      virt_dir_storage_pool_size: 20G
```

## License

[GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)
