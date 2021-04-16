# Cloudera Setup

## Provision Virtual Machines

The [Vagrantfile](./Vagrantfile) contains a parameter `N` that scales the number
of virtual machines. Issuing `vagrant up` will bootstrap those `N` virtual
machines

- cloudera0
- ...
- cloudera(N-1)

Each of them with

- Ubuntu 18.04
- 8 CPUs
- 12 GiB RAM
- 64 GiB HDD
- Private IP 10.0.0.{10+0..N-1}
- Internet via NAT

It will then provision those machines using the [Ansible Provisioner][AnsPro].
Among other things the [playbook](./playbook.yml) will

- Install System Updates
- Reboot if necessary
- Install and Configure System Requirements for Cloudera Manager Installer
- Download the Cloudera Manager Installer for the `vagrant` User at `cloudera0`

## Cloudera Manager Installer

Log onto `cloudera0` by issuing `vagrant ssh cloudera0` and run the [Cloudera
Manager Installer][CloMan]:

```bash
sudo ./cloudera-manager-installer.bin
```

## Install Cloudera Runtime

- Point your Web Browser at `http://10.0.0.10:7180` and [install Cloudera
  Runtime][RunTim]. 
- Specify Hosts: `cloudera[0-(N-1)]`
- Enter Login Credentials
  - Another User: `vagrant`
  - All hosts accept same password: `vagrant`

[VagFil]: https://www.vagrantup.com/docs/vagrantfile
[AnsPro]: https://www.vagrantup.com/docs/provisioning/ansible
[CloMan]: https://docs.cloudera.com/cdp-private-cloud-base/7.1.6/installation/topics/cdp-quick-start-streams-run-cm-server-installer.html
[RunTim]: https://docs.cloudera.com/cdp-private-cloud-base/7.1.6/installation/topics/cdp-quick-start-deployment-streams-install-runtime.html
