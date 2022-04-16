## Ansible Facts

- Ansible facts are the host-specific system data and properties of your target nodes system which includes operating systems, IP addresses, attached filesystems etc

- Ansible facts are stored in JSON format and are used to make important decisions about tasks based on their statistics.

- Facts are stored in an **ansible_facts** variable, which is managed by Ansible Engine and can be accessed.

- You can also access some Ansible facts as top-level variables with the **ansible\_** prefix.

- Ansible Facts are the default first task which will be triggered to gather all the data of you target nodes unless you specify not to do so.

**Playbook Exmaple 1** :

![image](https://drive.google.com/uc?export=view&id=1O0e0A16N7k9i9mpO4mPbvJkDoq9GBvEd)

**Playbook Exmaple 1 Explanation** : Here in **example-1-ansible-facts.yaml**, we have only 1 task which is using debug module.

**Task 1** : Name of task 1 is **"ansible facts variables"**. It is using debug module and printing the JSON data stored in **ansible_facts** variable.

**To Run the Playbook** :

```
ansible-playbook example-1-ansible-facts.yaml
```

**Output** :

```
PLAY [ansible facts example playbook] ******************************************************************************************************************************************

TASK [Gathering Facts]*********************************************************************************************************************************************************
ok: [target-node1]

TASK [ansible facts variables] *************************************************************************************************************************************************
ok: [target-node1] => {
    "msg": {
        "all_ipv4_addresses": [
            "10.0.2.15",
            "192.168.56.11"
        ],
        "all_ipv6_addresses": [
            "fe80::d0:90ff:fef5:1171",
            "fe80::a00:27ff:feb1:b13f"
        ],
        "ansible_local": {},
        "apparmor": {
            "status": "enabled"
        },
        "architecture": "x86_64",
        "bios_date": "12/01/2006",
        "bios_vendor": "innotek GmbH",
        "bios_version": "VirtualBox",
        "board_asset_tag": "NA",
        "board_name": "VirtualBox",
        "board_serial": "NA",
        "board_vendor": "Oracle Corporation",
        "board_version": "1.2",
        "chassis_asset_tag": "NA",
        "chassis_serial": "NA",
        "chassis_vendor": "Oracle Corporation",
        "chassis_version": "NA",
        "cmdline": {
            "BOOT_IMAGE": "/boot/vmlinuz-4.15.0-175-generic",
            "console": "ttyS0",
            "ro": true,
            "root": "UUID=b9b3ed0b-d494-4c3d-8e98-c9d4adc74449"
        },
        "date_time": {
            "date": "2022-04-10",
            "day": "10",
            "epoch": "1649616177",
            "hour": "18",
            "iso8601": "2022-04-10T18:42:57Z",
            "iso8601_basic": "20220410T184257990466",
            "iso8601_basic_short": "20220410T184257",
            "iso8601_micro": "2022-04-10T18:42:57.990466Z",
            "minute": "42",
            "month": "04",
            "second": "57",
            "time": "18:42:57",
            "tz": "UTC",
            "tz_dst": "UTC",
            "tz_offset": "+0000",
            "weekday": "Sunday",
            "weekday_number": "0",
            "weeknumber": "14",
            "year": "2022"
        },
        "default_ipv4": {
            "address": "10.0.2.15",
            "alias": "enp0s3",
            "broadcast": "10.0.2.255",
            "gateway": "10.0.2.2",
            "interface": "enp0s3",
            "macaddress": "02:d0:90:f5:11:71",
            "mtu": 1500,
            "netmask": "255.255.255.0",
            "network": "10.0.2.0",
            "type": "ether"
        },
        "default_ipv6": {},
        "device_links": {
            "ids": {},
            "labels": {
                "sda1": [
                    "cloudimg-rootfs"
                ],
                "sdb": [
                    "cidata"
                ]
            },
            "masters": {},
            "uuids": {
                "sda1": [
                    "b9b3ed0b-d494-4c3d-8e98-c9d4adc74449"
                ],
                "sdb": [
                    "2022-03-08-22-27-43-00"
                ]
            }
        },
        "devices": {
            "loop0": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "4096",
                "vendor": null,
                "virtual": 1
            },
            "loop1": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "loop2": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "loop3": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "loop4": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "loop5": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "loop6": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "loop7": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "none",
                "sectors": "0",
                "sectorsize": "512",
                "size": "0.00 Bytes",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "sda": {
                "holders": [],
                "host": "SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": "HARDDISK",
                "partitions": {
                    "sda1": {
                        "holders": [],
                        "links": {
                            "ids": [],
                            "labels": [
                                "cloudimg-rootfs"
                            ],
                            "masters": [],
                            "uuids": [
                                "b9b3ed0b-d494-4c3d-8e98-c9d4adc74449"
                            ]
                        },
                        "sectors": "83883999",
                        "sectorsize": 512,
                        "size": "40.00 GB",
                        "start": "2048",
                        "uuid": "b9b3ed0b-d494-4c3d-8e98-c9d4adc74449"
                    }
                },
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "cfq",
                "sectors": "83886080",
                "sectorsize": "512",
                "size": "40.00 GB",
                "support_discard": "0",
                "vendor": "VBOX",
                "virtual": 1
            },
            "sdb": {
                "holders": [],
                "host": "SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI",
                "links": {
                    "ids": [],
                    "labels": [
                        "cidata"
                    ],
                    "masters": [],
                    "uuids": [
                        "2022-03-08-22-27-43-00"
                    ]
                },
                "model": "HARDDISK",
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "cfq",
                "sectors": "20480",
                "sectorsize": "512",
                "size": "10.00 MB",
                "support_discard": "0",
                "vendor": "VBOX",
                "virtual": 1
            }
        },
        "discovered_interpreter_python": "/usr/bin/python",
        "distribution": "Ubuntu",
        "distribution_file_parsed": true,
        "distribution_file_path": "/etc/os-release",
        "distribution_file_variety": "Debian",
        "distribution_major_version": "18",
        "distribution_release": "bionic",
        "distribution_version": "18.04",
        "dns": {
            "nameservers": [
                "127.0.0.53"
            ],
            "options": {
                "edns0": true
            }
        },
        "domain": "",
        "effective_group_id": 1000,
        "effective_user_id": 1000,
        "enp0s3": {
            "active": true,
            "device": "enp0s3",
            "features": {
                "esp_hw_offload": "off [fixed]",
                "esp_tx_csum_hw_offload": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "off [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "off [fixed]",
                "netns_local": "off [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off",
                "rx_checksumming": "off",
                "rx_fcs": "off",
                "rx_udp_tunnel_port_offload": "off [fixed]",
                "rx_vlan_filter": "on [fixed]",
                "rx_vlan_offload": "on",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "off [fixed]",
                "tx_checksumming": "on",
                "tx_esp_segmentation": "off [fixed]",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipxip4_segmentation": "off [fixed]",
                "tx_ipxip6_segmentation": "off [fixed]",
                "tx_lockless": "off [fixed]",
                "tx_nocache_copy": "off",
                "tx_scatter_gather": "on",
                "tx_scatter_gather_fraglist": "off [fixed]",
                "tx_sctp_segmentation": "off [fixed]",
                "tx_tcp6_segmentation": "off [fixed]",
                "tx_tcp_ecn_segmentation": "off [fixed]",
                "tx_tcp_mangleid_segmentation": "off",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "on [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "off",
                "vlan_challenged": "off [fixed]"
            },
            "hw_timestamp_filters": [],
            "ipv4": {
                "address": "10.0.2.15",
                "broadcast": "10.0.2.255",
                "netmask": "255.255.255.0",
                "network": "10.0.2.0"
            },
            "ipv6": [
                {
                    "address": "fe80::d0:90ff:fef5:1171",
                    "prefix": "64",
                    "scope": "link"
                }
            ],
            "macaddress": "02:d0:90:f5:11:71",
            "module": "e1000",
            "mtu": 1500,
            "pciid": "0000:00:03.0",
            "promisc": false,
            "speed": 1000,
            "timestamping": [
                "tx_software",
                "rx_software",
                "software"
            ],
            "type": "ether"
        },
        "enp0s8": {
            "active": true,
            "device": "enp0s8",
            "features": {
                "esp_hw_offload": "off [fixed]",
                "esp_tx_csum_hw_offload": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "off [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "off [fixed]",
                "netns_local": "off [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off",
                "rx_checksumming": "off",
                "rx_fcs": "off",
                "rx_udp_tunnel_port_offload": "off [fixed]",
                "rx_vlan_filter": "on [fixed]",
                "rx_vlan_offload": "on",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "off [fixed]",
                "tx_checksumming": "on",
                "tx_esp_segmentation": "off [fixed]",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipxip4_segmentation": "off [fixed]",
                "tx_ipxip6_segmentation": "off [fixed]",
                "tx_lockless": "off [fixed]",
                "tx_nocache_copy": "off",
                "tx_scatter_gather": "on",
                "tx_scatter_gather_fraglist": "off [fixed]",
                "tx_sctp_segmentation": "off [fixed]",
                "tx_tcp6_segmentation": "off [fixed]",
                "tx_tcp_ecn_segmentation": "off [fixed]",
                "tx_tcp_mangleid_segmentation": "off",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "on [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "off",
                "vlan_challenged": "off [fixed]"
            },
            "hw_timestamp_filters": [],
            "ipv4": {
                "address": "192.168.56.11",
                "broadcast": "192.168.56.255",
                "netmask": "255.255.255.0",
                "network": "192.168.56.0"
            },
            "ipv6": [
                {
                    "address": "fe80::a00:27ff:feb1:b13f",
                    "prefix": "64",
                    "scope": "link"
                }
            ],
            "macaddress": "08:00:27:b1:b1:3f",
            "module": "e1000",
            "mtu": 1500,
            "pciid": "0000:00:08.0",
            "promisc": false,
            "speed": 1000,
            "timestamping": [
                "tx_software",
                "rx_software",
                "software"
            ],
            "type": "ether"
        },
        "env": {
            "DBUS_SESSION_BUS_ADDRESS": "unix:path=/run/user/1000/bus",
            "HOME": "/home/vagrant",
            "LANG": "C.UTF-8",
            "LOGNAME": "vagrant",
            "MAIL": "/var/mail/vagrant",
            "PATH": "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin",
            "PWD": "/home/vagrant",
            "SHELL": "/bin/bash",
            "SHLVL": "1",
            "SSH_CLIENT": "192.168.56.1 59847 22",
            "SSH_CONNECTION": "192.168.56.1 59847 192.168.56.11 22",
            "SSH_TTY": "/dev/pts/1",
            "TERM": "xterm-256color",
            "USER": "vagrant",
            "XDG_RUNTIME_DIR": "/run/user/1000",
            "XDG_SESSION_ID": "62",
            "_": "/bin/sh"
        },
        "fibre_channel_wwn": [],
        "fips": false,
        "form_factor": "Other",
        "fqdn": "ubuntu-bionic",
        "gather_subset": [
            "all"
        ],
        "hostname": "ubuntu-bionic",
        "hostnqn": "",
        "interfaces": [
            "enp0s3",
            "lo",
            "enp0s8"
        ],
        "is_chroot": false,
        "iscsi_iqn": "",
        "kernel": "4.15.0-175-generic",
        "kernel_version": "#184-Ubuntu SMP Thu Mar 24 17:48:36 UTC 2022",
        "lo": {
            "active": true,
            "device": "lo",
            "features": {
                "esp_hw_offload": "off [fixed]",
                "esp_tx_csum_hw_offload": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "on [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "on [fixed]",
                "netns_local": "on [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off [fixed]",
                "rx_checksumming": "on [fixed]",
                "rx_fcs": "off [fixed]",
                "rx_udp_tunnel_port_offload": "off [fixed]",
                "rx_vlan_filter": "off [fixed]",
                "rx_vlan_offload": "off [fixed]",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on [fixed]",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "on [fixed]",
                "tx_checksumming": "on",
                "tx_esp_segmentation": "off [fixed]",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipxip4_segmentation": "off [fixed]",
                "tx_ipxip6_segmentation": "off [fixed]",
                "tx_lockless": "on [fixed]",
                "tx_nocache_copy": "off [fixed]",
                "tx_scatter_gather": "on [fixed]",
                "tx_scatter_gather_fraglist": "on [fixed]",
                "tx_sctp_segmentation": "on",
                "tx_tcp6_segmentation": "on",
                "tx_tcp_ecn_segmentation": "on",
                "tx_tcp_mangleid_segmentation": "on",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "off [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "off",
                "vlan_challenged": "on [fixed]"
            },
            "hw_timestamp_filters": [],
            "ipv4": {
                "address": "127.0.0.1",
                "broadcast": "",
                "netmask": "255.0.0.0",
                "network": "127.0.0.0"
            },
            "ipv6": [
                {
                    "address": "::1",
                    "prefix": "128",
                    "scope": "host"
                }
            ],
            "mtu": 65536,
            "promisc": false,
            "timestamping": [
                "tx_software",
                "rx_software",
                "software"
            ],
            "type": "loopback"
        },
        "lsb": {
            "codename": "bionic",
            "description": "Ubuntu 18.04.6 LTS",
            "id": "Ubuntu",
            "major_release": "18",
            "release": "18.04"
        },
        "machine": "x86_64",
        "machine_id": "26277375a223492ca8692576cad33fa0",
        "memfree_mb": 335,
        "memory_mb": {
            "nocache": {
                "free": 814,
                "used": 170
            },
            "real": {
                "free": 335,
                "total": 984,
                "used": 649
            },
            "swap": {
                "cached": 0,
                "free": 0,
                "total": 0,
                "used": 0
            }
        },
        "memtotal_mb": 984,
        "module_setup": true,
        "mounts": [
            {
                "block_available": 9685156,
                "block_size": 4096,
                "block_total": 10148403,
                "block_used": 463247,
                "device": "/dev/sda1",
                "fstype": "ext4",
                "inode_available": 5008755,
                "inode_total": 5120000,
                "inode_used": 111245,
                "mount": "/",
                "options": "rw,relatime,data=ordered",
                "size_available": 39670398976,
                "size_total": 41567858688,
                "uuid": "b9b3ed0b-d494-4c3d-8e98-c9d4adc74449"
            },
            {
                "block_available": 47402506,
                "block_size": 4096,
                "block_total": 122061322,
                "block_used": 74658816,
                "device": "/vagrant",
                "fstype": "vboxsf",
                "inode_available": 1000,
                "inode_total": 1000,
                "inode_used": 0,
                "mount": "/vagrant",
                "options": "rw,nodev,relatime",
                "size_available": 194160664576,
                "size_total": 499963174912,
                "uuid": "N/A"
            }
        ],
        "nodename": "ubuntu-bionic",
        "os_family": "Debian",
        "pkg_mgr": "apt",
        "proc_cmdline": {
            "BOOT_IMAGE": "/boot/vmlinuz-4.15.0-175-generic",
            "console": [
                "tty1",
                "ttyS0"
            ],
            "ro": true,
            "root": "UUID=b9b3ed0b-d494-4c3d-8e98-c9d4adc74449"
        },
        "processor": [
            "0",
            "GenuineIntel",
            "Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz",
            "1",
            "GenuineIntel",
            "Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz"
        ],
        "processor_cores": 2,
        "processor_count": 1,
        "processor_nproc": 2,
        "processor_threads_per_core": 1,
        "processor_vcpus": 2,
        "product_name": "VirtualBox",
        "product_serial": "NA",
        "product_uuid": "NA",
        "product_version": "1.2",
        "python": {
            "executable": "/usr/bin/python",
            "has_sslcontext": true,
            "type": "cpython",
            "version": {
                "major": 3,
                "micro": 9,
                "minor": 6,
                "releaselevel": "final",
                "serial": 0
            },
            "version_info": [
                3,
                6,
                9,
                "final",
                0
            ]
        },
        "python_version": "3.6.9",
        "real_group_id": 1000,
        "real_user_id": 1000,
        "selinux": {
            "status": "disabled"
        },
        "selinux_python_present": true,
        "service_mgr": "systemd",
        "ssh_host_key_dsa_public": "AAAAB3NzaC1kc3MAAACBALtg3OTjxrow9HjciGdLwQMNuDUwCoT1sns34GPxbm9iqxQSR7Q5HluTW22TN4S+FfHuJxO4yOgSbu11mssgKduC9JfkZwVBzw4oxxuifRuvjp80KCm4hnIMCnK/rf/sUF1lc3L/cxe/ne9Lysr0xLMMQ5TuxYTRT1AIU6ogBDwVAAAAFQCSq7x364vA7Ffr0c4AsjMUPBD+nQAAAIBxfjKtBiiAfR+duiUMo823oUQLUk52fnlEsGbvTIQA0w1C0KSZ2s24nm7tJLVcI/u7El4fqbYWRIuN4Q1x5534pIiQOVGTWbPu/RSBQT2Rkl5kYq/FDQvb4OjvCs3wY9wlb94zmIvIHGQNfNX3wus994Dbs7i3HG5M0RfkZa7eBAAAAIEAq3DDQWMIA05hMn7f9av0uUOLmY71cXwTrIME28sPXp4rS/mItju4joE3+E5NDNOzMnQ88ysH2tb2LA3Zr0nO0vPWo8G2DU127SoAkcDw+uuZO1Gs7zfhyS7U5I7IWM3Bo/GCOsQuOm00N+tljyRmRmGYbCgsyjGCSGA4kFP9dZk=",
        "ssh_host_key_dsa_public_keytype": "ssh-dss",
        "ssh_host_key_ecdsa_public": "AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBPd5I5ApfnXMa8W5HTjloErJNA0hjUB3Ig/mH0aWoZXr6AQpGe9rteni8pB1d42FxDWx9ReZyM7hn5zC773ZrgY=",
        "ssh_host_key_ecdsa_public_keytype": "ecdsa-sha2-nistp256",
        "ssh_host_key_ed25519_public": "AAAAC3NzaC1lZDI1NTE5AAAAIEhf8IjnzsUiYH2yKILAlva3jambhIRv0JM1nkkNkaeu",
        "ssh_host_key_ed25519_public_keytype": "ssh-ed25519",
        "ssh_host_key_rsa_public": "AAAAB3NzaC1yc2EAAAADAQABAAABAQDQ5HJ15NlQAI338iMqPn6bZWyXuc3sS0ReVj9HaXIEafIANTVDvBQt6BbdTB5bxyCHscSrCZSYLktu6f+C4RZ/laKT29QOr3H7fSFLE08CaZsQfvdboeJXkxFXy6zXk3nGPyOH8I4/lsWun0FnwGXxmDWFw+tLz61unSWJ+h4p7R9Xx43JG1UUdSYRnHijr90ujC3GTTIiZLPYJ0JuywPO9DfYeNMxKQLr7xIhQhoRrrVSiCTqScjuAcgvvmiACegvGEKqjmJQdZg0iPZIGUAxlB2uIbG9bNxzdatHkfz3tDN35CxAnluysCRN6CAHt2XSGcvr4YJ7GAhvcnVEvqUL",
        "ssh_host_key_rsa_public_keytype": "ssh-rsa",
        "swapfree_mb": 0,
        "swaptotal_mb": 0,
        "system": "Linux",
        "system_capabilities": [
            ""
        ],
        "system_capabilities_enforced": "True",
        "system_vendor": "innotek GmbH",
        "uptime_seconds": 45568,
        "user_dir": "/home/vagrant",
        "user_gecos": ",,,",
        "user_gid": 1000,
        "user_id": "vagrant",
        "user_shell": "/bin/bash",
        "user_uid": 1000,
        "userspace_architecture": "x86_64",
        "userspace_bits": "64",
        "virtualization_role": "guest",
        "virtualization_tech_guest": [
            "virtualbox"
        ],
        "virtualization_tech_host": [],
        "virtualization_type": "virtualbox"
    }
}

PLAY RECAP *********************************************************************************************************************************************************************
target-node1               : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

**Note** : In above output, you can see that the first task is **"TASK [Gathering Facts]"** which is the default behaviour and then running the next task **"TASK [ansible facts variables]"** which we have written in our ansible playbook.

**Filtering Specific Value Ansible Facts Data**

Now, you have already seen how much data Ansible Facts stores and we might not need all of this, so we can filter out the values as per our requirements.

Suppose, if you want to see the user directory of the target node where you are running your playbook.

**Playbook Exmaple 2** :

![image](https://drive.google.com/uc?export=view&id=1rsrfnbipwGeQ4xzGXhZLNK8eh5jV34A-)

**Playbook Exmaple 2 Explanation** : Here in **example-2-ansible-facts-filter-values.yaml**, we have only 1 task which is using debug module to print the filtered value from ansible facts.

**Task 1** : Name of task 1 is **"ansible facts variables"**. It is using debug module and printing the user directory data stored in **ansible_facts** variable. **user_dir** which is used in this task to filter the data can be seen in the previous ansible playbook output where we have all the data stored in Ansible Facts.

**To Run the Playbook** :

```
ansible-playbook example-2-ansible-facts-filter-values.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=1nbktFfqkzQGeq9VGrVu3egNBFsU-spqI)

**Disabling Ansible Facts**

You can disable Ansible Facts to gather the data of your target nodes, if you know all about your target machines. Disabling facts improves performance in push mode when you have large number of systems in place.

Syntax :

```
hosts: target-nodes
gather_facts: no
```

**Playbook Exmaple 3** :

![image](https://drive.google.com/uc?export=view&id=1e1gwloR5jT8ft2G0W88J-QeXn235Rr1D)

**Playbook Exmaple 3 Explanation** : Here in **example-3-disable-facts.yaml**, we have only 1 task which is using debug module to print the data stored in ansible facts variable.

**Task 1** : Name of task 1 is **"ansible facts variables"**. It is using debug module and printing all the data stored in **ansible_facts** variable. But since we have disabled ansible facts to gather any data, we can see empty json response in the output.

**To Run the Playbook** :

```
ansible-playbook example-3-disable-facts.yaml
```

**Output** :

![image](https://drive.google.com/uc?export=view&id=180wXYxCDsxeXuzL9MUM5MfCrm-7oqIT1)

**Note** : Also, notice in the output thet we don't have any task like **"TASK [Gathering Facts]"**, as we have disabled facts.

**Exercises** : Check your knowledge

Please check **exercises** file added in this lesson and try to complete it.
