# Terraform
[Terraform](https://www.terraform.io/) is open source tool used for automation and management of your infrastructure (provisioning). 

Uses declarative approach for configuration files - defines the ___end state___ of your infrastracture. This gives benefits when ___updating___ the infrastracture.
Adjust old config file and re-execute vs adding new setup instractions (imperative style). Shows final state, not instructions how to get there.  

## Terraform vs Ansible
Both IaaC, both automate provisioning, configuring and managing the infrastracture. It is a common practice to combine these two:

A, Start with Terraform for provisioning, then use Terraform once infrastructure is ready to call Ansible to do configuration management.

B, Start with Ansible, first step in playbook call Terraform to setup infrastructure, then pickup where Terraform leaves of and configure the infrastructure.

### Terraform
- Mainly infrastracture privisioning tool
- Can deploy apps
- Relatively new
- More advanced in orchestration
- Declarative style
- Works with state
- Is idempotent automatically

__Better for infrastructure.__

### Ansible
- Mainly a configuration tool
- Configure the infrastructure
- Deploy apps
- Install/Update software
- More mature
- Procedural style (kind of hybrid)
- You need to implement steps
- Idempotency is not required, but can be implemented

__Better for configuring that infrastructure.__

### Similarities
- Support heavy templating
- Open source projects
- Agentless - you don't install agent - both plug and play tools

## Terraform use cases
Create infrastructure.  
Change infrastructure.  
Replicate infrastructure.

## Terraform Architecture
Two main components:

### CORE
Uses two input sources:  
1. TF-Config  
Define resources and its attributes  
Created by user - define what to create/configure  
Example file:
```terraform
# Configure the AWS Provider
provider "aws" {
    version = "~> 2.0"
    region = "us-east-1"
}

# Create a VPC
resource "aws-vpc" "example" {
    cidr_block = "10.0.0.0/16"
}
```
2. State  
Up to date state of current setup of infrastructure

Terraform creates execution plan - what needs to be created/updated/destroyed - based on these two sources.

### Providers
For specific technology:
1. Cloud providers AWS|AZURE|IaaS
2. Kubernetes|PaaS
3. Fastly|SaaS  

Over 100 providers, over 1000 resources. Providers give access to resources, ie. AWS provider > EC2 instances.  
Core creates execution plan > providers execute it on desired platform.

## Terraform commands
Has different commands for different stages.  
1. refresh  
Query infrastructure provider to get current state. Gets up to date state.
2. plan  
Create an exectuion plan. Determines what actions are necessary to achieve the desired state. Just a plan - not an actual changes done.
3. apply  
Execute the plan. When `apply` commandis executed, terraform will automatically execute `refresh` and `plan` commands.
4. destroy
Destroy the resources/infrastracture.  When `destroy` command is executed, terraform will automatically execute `refresh` and `plan` commands.


## Sources
[Terraform explained in 15 mins | Terraform Tutorial for Beginners - TechWorld with Nana](https://www.youtube.com/watch?v=l5k1ai_GBDE)  
[Ansible vs. Terraform: What's the difference? - IBM Technology](https://www.youtube.com/watch?v=rx4Uh3jv1cA)
