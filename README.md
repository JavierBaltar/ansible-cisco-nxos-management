# ansible-cisco-nxos-management
This repository provides playbooks for managing Cisco NX-OS devices

<p align="center">
  <a href="#Getting-Started">Getting Started</a> •
  <a href="#Playbooks">Playbooks</a> •
  <a href="#Related">Related</a> •
  <a href="#Authors">Authors</a>
</p>

## Getting Started

The playbooks are tested using Ansible and AWX with 

## Playbooks

### Create VLANs
```yaml
  tasks:
    - name: Ensure VLAN 2 and 3 exist
      nxos_vlan: vlan_id="2,3" state=present host={{ inventory_hostname }}

    - name: Configure VLAN names
      nxos_vlan: vlan_id={{ item.vid }} name={{ item.name }} host={{ inventory_hostname }} state=present
      with_items:
        - { vid: 2, name: database }
        - { vid: 3, name: application }
```

### Run Show Version
```yaml

  - name: Test reachability to Ansible host
    ios_ping:
      dest: 10.0.0.1

  - name: Run show version
    ios_command:
      commands:
        - show version
    register: version
   
- debug: var=version.stdout_lines
```

## Related

* [Ansible](https://www.ansible.com) - Configuration Management
* [AWX](https://github.com/ansible/awx) - Configuration Management
 

## Authors

* **Javier Baltar** - *Initial work* - [GitHub](https://github.com/JavierBaltar)
