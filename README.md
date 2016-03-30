## Ansible playbook for owncloud with ZFS and docker

This playbook installs owncloud using two docker containers from the Docker Hub: owncloud and mysql.

After a successful run, you should be able to access owncloud at the following address:

    https://<docker-host-ip>:8001

Where docker-host-ip must be configured in the `hosts` file and the admin password must be configured in the `vars.yml` file.

Owncloud will be setup with the following features:

* Use mysql as database (instead of sqlite3)
* Use APCu for cache
* Use secure HTTPS connection with a self-signed certificate (ssl-cert package)
* Store data on a ZFS filesystem identified by the `owncloud_zfs_fs_data` variable

## Assumptions

* Fresh install of Ubuntu with a ZFS zpool available (its name to be assigned to the `zpool_name` variable)
* Passwordless sudo for ansible to work
* Python 2.7 on the host (Ubuntu 16.04 may come with Python 3 only)

## How to use the playbook

* Configure the hosts in the `hosts` file
* Configure the variables in the `vars.yml` file
* Run the playbook with something like
      ansible-playbook -i hosts site.yml
