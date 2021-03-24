# Manage Configlets in CVP

Update configlets and attach them to Devices in CVP

## Pre-Requisites

Install Arista AVD and CVP Collections and update ansible.cfg collections path.

```text
git clone https://github.com/aristanetworks/ansible-avd.git
git clone https://github.com/aristanetworks/ansible-cvp.git
```

## Recommended to run Docker Container

This repo has instructions on how to build a dcoker image and run it as a container.  All Ansible modules and collections are included.

```text
git clone https://github.com/mthiel117/dockerbuild.git
```

## Summary of Steps

1. Update datafiles/devices.csv with devices to create base configlets
2. Update Device List in host_vars/cvp/device_inventory.yml
3. Run playbook to create base configlets
4. Run playbook to update configlets in CVP and attach them to the devices

## Run Playbooks

Create Base Configlets

```text
ansible-playbook playbooks/create_base_configs.yml
```

Upload Configlets to CVP and Attach to Device

```text
ansible-playbook playbooks/update_configlets.yml --tags "update,provison"
```