mysql-box
=========

Underlying ansible roles: `sa-node`, `sa-node-nvm`.  Check roles documentation for whole set of parameters to override.

Supported tags:

`sa_node`, `sa_node_nvm`


Referencing as dependency using gilt (https://github.com/metacloud/gilt/,  `pip install python-gilt`)

```
# https://gilt.readthedocs.io/en/latest/
  - git: https://github.com/oops-to-devops/node-box.git
    version: master
    dst: deployment/provisioners/node-box/
    post_commands:
      - make
```


Supported parameters overrides:


```
```


Using with vagrant boilerplate (https://github.com/Voronenko/devops-vagrant-ansible-boilerplate)

```ruby

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "deployment/provisioners/node-box/box_node.yml"
        ansible.galaxy_role_file = "deployment/provisioners/node-box/requirements.yml"
        ansible.galaxy_roles_path = "deployment/provisioners/node-box/roles"
        ansible.verbose = true
        ansible.groups = {
            "node_box" => [vconfig['vagrant_machine_name']]
        }
        # ansible.tags = ["sa_mysql"]
        ansible.extra_vars = {
            box_provider: "vagrant",
            env: "vagrant"
        }
    end


```
