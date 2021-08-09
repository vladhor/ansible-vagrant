# Ansible Local Test Environment using Vagrant 
This code is used to to create test ansible environment with one Controlnode and five managed hosts.

 Box         |     OS        | Hostname (FQDN)
-------------|---------------|----------------
Controlnode  | CentOS 8.3    | control
Node-1       | CentOS 8.3    | node-1
Node-2       | CentOS 8.3    | node-2
Node-3       | CentOS 8.3    | node-3
Node-4       | CentOS 8.3    | node-4
Node-5       | CentOS 8.3    | node-5

## Requirements
The following applications must already be installed
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Vagrant](https://www.vagrantup.com/downloads)

## Installation
Clone the project
```bash
$ git clone https://github.com/vladhor/vagrant-ansible.git
 
```

## Start environment
Enter cloned project
```bash
$ cd vagrant-ansible
```
Start and provisions the vagrant environment
```bash
$ vagrant up 
```
## Additional commands 
Check status of the vagrant machines 
```bash
$ vagrant status
```
Connects to vagrant machine as a ansible user
```bash
$ vagrant ssh controlnode
```
Stops and deletes all traces of the vagrant machines
```bash
$ vagrant destroy
```
After the deploy, if you change something inside of provisioning script, you can apply it without destroy and recreate the VM by:
```bash
$ vagrant up --provision
```
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## Authors
**vladhor** - *Initial work* - [vladhor](https://github.com/vladhor)

## License
This project is licensed under the  GNU GENERAL PUBLIC LICENSE Version 3 License - see the [LICENSE.md](https://github.com/vladhor/vagrant-ansible/blob/main/LICENSE.md) file for details
