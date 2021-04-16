# Cloudera Setup

## Provision Virtual Machines

Issuing `vagrant up` will bootstrap three virtual machines

- cloudera0
- cloudera1

Each of them with

- Ubuntu 18.04
- 8 CPUs
- 12 GiB RAM
- 64 GiB HDD
- Private IP 10.0.0.1{0..N-1}
- Internet via NAT

It will then

- Install System Updates
- Reboot if necessary
- Install System Requirements for Cloudera Manager Installer
- Download the Cloudera Manager Installer

## Cloudera Manager Installer

Log onto `cloudera1` by issuing `vagrant ssh cloudera1` and [run the
installer][install]:

```bash
sudo ./cloudera-manager-installer.bin
```

## Install Cloudera Runtime

- Point your Web Browser at `http://10.0.0.11:7180` and [install Cloudera
  Runtime][runtime]. 
- Specify Hosts: `cloudera[0-(N-1)]`
- Enter Login Credentials
  - Another User: `vagrant`
  - All hosts accept same password: `vagrant`

[install]: https://docs.cloudera.com/cdp-private-cloud-base/7.1.6/installation/topics/cdp-quick-start-streams-run-cm-server-installer.html
[runtime]: https://docs.cloudera.com/cdp-private-cloud-base/7.1.6/installation/topics/cdp-quick-start-deployment-streams-install-runtime.html
