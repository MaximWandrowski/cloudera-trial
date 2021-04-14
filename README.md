# Cloudera Setup

## Provision Virtual Machines

Issuing `vagrant up` will bootstrap three virtual machines

- cloudera1
- cloudera2
- cloudera3

Each of them with

- Ubuntu 18.04
- 8 CPUs
- 8 GiB RAM
- 64 GiB HDD
- Private IP 10.0.0.1{1..N}
- Internet via NAT

It will then

- Install System Updates
- Reboot if necessary
- Install system requirements for the Cloudera Manager Installer
- Download the Cloudera Manager Installer

## Cloudera Manager Installer

Log onto `cloudera1` by issuing `vagrant ssh cloudera1` and [run the
installer][install]:

```bash
sudo ./cloudera-manager-installer.bin
```

Point your Web Browser at `http://10.0.0.11:7180` and [install Cloudera
Runtime][runtime].

[install]: https://docs.cloudera.com/cdp-private-cloud-base/7.1.6/installation/topics/cdp-quick-start-streams-run-cm-server-installer.html
[runtime]: https://docs.cloudera.com/cdp-private-cloud-base/7.1.6/installation/topics/cdp-quick-start-deployment-streams-install-runtime.html
