# ansible_examples

A small collection of example Ansible playbooks/roles/modules

==Please Note: These examples have been taken out of context and are non-functional as they exist in this repository!==

### build_vm
* build_vm.yml is the major functionality of a role which is responsible for building VM infrastructure from image based provisioning to configuration management utilizing Puppeyt and Foreman.  
* build_vm.yml calls the `terraform` role (included) which uses jinja2 templating to generate the Terraform TF files and creates/destroys the infrastructure as defined.


### health_validation
* Ansible playbook to smoke test external services which are critical to environment build process.
* Runs any task file that matches `*-test.yml`, processes the result and reports the status of all tests ran.
* Runs on a schedule and disables builds if any critical service is down and creates a support ticket.
    * Note: This functionality is not included here, but I thought it was valuable context.

### f5_query Module ###
* Ansible python module that queries F5 LTM/GTM devices and returns all objects of the specified type
* The biggest benefit of this module is the REST calls handle pagination which increases performance and stability

```
f5_query
  f5_url: 'https://{{ f5-url }}//mgmt/tm/ltm/virtual'
  username: {{ username }}
  password: {{ password }}
  page_size: 100
```

