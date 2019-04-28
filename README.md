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

### Change MGCP Agent
```yaml
tasks:
     - ios_config:
          provider: "{{login_info}}" 
          lines:
            - mgcp call-agent 10.0.0.10
          before: "no mgcp call-agent 10.0.0.9"  
       
     - ios_config:
          save: yes
          provider: "{{login_info}}"
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
