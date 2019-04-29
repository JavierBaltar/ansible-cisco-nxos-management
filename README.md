# ansible-cisco-nxos-management
This repository provides playbooks for managing Cisco NX-OS devices

<p align="center">
  <a href="#Getting-Started">Getting Started</a> •
  <a href="#Playbooks">Playbooks</a> •
  <a href="#Related">Related</a> •
  <a href="#Authors">Authors</a>
</p>

## Getting Started

The playbooks are tested using Ansible and AWX

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

### Configure Portchannels
```yaml
tasks:
    - name: Create portchannel 200
      nxos_portchannel:
        group: 200
        members: ['Ethernet1/1','Ethernet1/2']
        mode: 'active'
        host: "{{ inventory_hostname }}"
        state: present
```

### Feature Enablement
```yaml
tasks:
    - name: Ensure DHCP is enabled
      nxos_feature:
        feature: dhcp
        state: enabled
        host: "{{ inventory_hostname }}"
        
```

## Related

* [Ansible](https://www.ansible.com) - Configuration Management
* [AWX](https://github.com/ansible/awx) - Configuration Management
 

## Authors

* **Javier Baltar** - *Initial work* - [GitHub](https://github.com/JavierBaltar)
