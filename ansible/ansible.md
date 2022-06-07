# Ansible
[Ansible](https://www.ansible.com/) is an open source (agentless) infrastracture automation tool initially developed by Red Hat.

Ansible uses so called 'playbooks' (`yaml` files). Each playbook contains 'play'. Each play consists of name for the 'play', 'host' that it runs against, the actual 'task' to run. Actions you want to run multiple times can be grouped to 'roles'.

Ansible supports all infrastracture - all OS, cloud providers, bare metal infrastructure...


## Ansible use cases
### Provisioning


### Config management
Main use case. Ability to configure infrastracture - OS patches, install some services, run services etc. 

### App deployment
Deploy an actual application to virtual machines

## Ansible components
### Modules
Small programs that do the actual work. Pushed from control machine to target server where they do the actual work. Very granular - one module = one small specific task - ie. install docker container, create cloud instance, install nginx server...

Example of jenkins module:
```yaml
- name: Create a jenkins job using basic authentication
  community.general.jenkins_job:
    config: "{{ lookup('file', 'templates/test.xml') }}"
    name: test
    password: admin
    url: http://localhost:8080
    user: admin
```

### Playbook
Playbook contains one or more plays. Play is a sequence of modules grouped in tasks run on a host.

Example of a database play:
```yaml
- name: rename table, set owner and truncate it
- hosts: databases
  remote_user: root
  
  tasks:
    - name: Rename table foo to bar
      postgresql_table:
        table: foo
        renam: bar
      
    - name: Set owner to someuser
      postgresql_table:
        name: foo
        owner: someuser
      
    -name: Truncate table foo
     postgresql_table:
        name: foo
        truncate: yes
```
Variables can be used.

### Ansible Inventory
File with hosts specified.

Example of inventory:
```yaml
10.24.0.100

[webservers]
10.24.0.1
10.24.0.2

[databases]
10.24.0.8
10.24.0.9
```
Can contain IP addresses or hostnames.

## Ansible for Docker
Usually Dockerfile - alternative is Ansible Playbook, which is more powerful.

## Ansible Tower
UI dashboard from Red Hat.
* Centrally store automation tasks
* Across teams
* Configure permissions
* Manage inventory

## Ansible vs. Puppet vs. Chef
Ansible is more popular because:  
1, Uses simple YAML structure (Puppet/Chef use Ruby)  
2, Is agentless (Puppet and Chef need to be installed on target servers)

## Sources
[What is Ansible? - IBM Technology](https://www.youtube.com/watch?v=fHO1X93e4WA)  
[What is Ansible | Ansible Playbook explained | Ansible Tutorial for Beginners - TechWorld with Nana](https://www.youtube.com/watch?v=1id6ERvfozo)
