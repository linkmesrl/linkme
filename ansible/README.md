## Ansible getting started

This is a simple walk through to create a provisioning script for a development environment based on MEAN.

This will install and configure:

- MongoDB
- NodeJs
- Npm
- Git
- Pm2
- Nginx

## Ansible setup

To install Ansible on your machine run

```
brew update
brew install ansible
```

## Define the inventory file

Check out [this](./inventory) example.
 
The complete documentation is [here](http://docs.ansible.com/intro_inventory.html)

Once you have defined an `inventory` you can run commands on multiple target, for example:

```
ansible webservers -i inventory -m ping
```
__ This command will be executed in all the target listed in the `[webservers]` group defined in the inventory __

## Playbooks

**Playbooks** let you define a list of tasks to be executed on a `group`

The complete documentation is [here](http://docs.ansible.com/playbooks_intro.html)

The operations that are accomplished by this playbook are:

- Creating a `deploy` user
- Create two folders for **Server** in `/var/www/node` and **Client** in `/var/www/static`
- Install `nginx`, `git`, `nodejs`, `npm`
- Install [pm2](https://github.com/Unitech/pm2)
- Install `MongoDB`

To provision your virtual machine (based on Ubuntu 14.04)

```
ansible-playbook -i inventory -l webservers playbook.yml
```


### Next steps:

- Install and configure a basic `.vimrc`
- Configure default virtual host
