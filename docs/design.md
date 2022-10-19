# ansible-vmware-okd-centos8


## Introduction

    This guide is used to deploy clusters in VMware vsphere.

### References
    https://docs.okd.io/4.9/support/troubleshooting/troubleshooting-installations.html

### Software version

| Software | Version |
| --- | --- |
| `openshift` | *4.6.1*, *4.10.26* |
| `rhcos` | *4.6.1*, *4.10.26* |

### Architect

Process of installation 

![Deploy process](./diagrams/process1.png)

### Description

We prepare environment:
    - number of lab ( lab-#)
    - number of VM in a lab ( lab-#-vm-#)
    - network 1 : 10.1.17.0/16
    - subnet 1: 255.255.0.0
    - gateway 1: 10.1.0.1
    - network 2 : 192.168.126.0/24
    - subnet 2: 255.255.255.0
    - gateway 2: 192.168.126.1 
    - number IP in a lab: 10 

Playbook prepare_env.yml <br /> 
For simple service setup (include DNS, haproxy, DHCP) we still use same IP address and MAC address for VM. vsphere environement allow to create VMs with differents name and same MAC. However we can only run 1 OCP4 cluster at once time. <br />



## Prepare

Get pull secret variables from at https://console.redhat.com/openshift/install/metal/installer-provisioned/, then copy into my_pull_secret: '{"auths":....}' in prepare_ocp_ignition.yml file

### Prepare vsphere environment

Put user login into: vars/vmw_env.yml<br />
Put cluster VM info into: vars/<version>/vmw_vms.yml<br />
Download iso file and put to ISO datastore, then VM var will point the cdrom to that iso image. 

 

