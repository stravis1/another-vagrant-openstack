# another-vagrant-openstack

### Overview.
Done as an educational project to provide a simple Vagrant setup for launching VMs in OpenStack.

## SETUP: Begin by installing the following:

- Clone the repo: **git clone ssh://<user>@@github.com/<project-name>**
- Supported on MacOS 10.9 or later.
- **Install** Vagrant: 1.6.5 or later - <https://www.vagrantup.com/downloads.html>
- **Install these Vagrant plugins**
- - vagrant-openstack-provider >=(0.7.1)
- - vagrant-reload
- - vagrant-host-shell

```
vagrant plugin install vagrant-openstack-provider vagrant-vbox-snapshot

```
- **Install these Ruby gems:**

```
sudo gem install librarian-puppet-simple mustache
```
- **Install openstack client python-glanceclient:**

```
sudo easy_install python-glanceclient
```


#### SETUP PROJECT: 
- **Add your openrc file to this cloned repo** : Uses horizon to download a copy of your openrc
  file for one of your user/tenant combos that MUST NOT have the admin role.
  Place the openrc file within your cloned repo.
- **Add to your openrc file**: 
  Add: "export VAGRANT_DEFAULT_PROVIDER=openstack” to your openrc file.
- **Source openrc** Source your openrc to enable the openstack provider.
  This will configure vagrant to start nodes using the openstack provider and
  allow you to verify instance status using the nova/neutron CLI.
  Only the horizon generated specific source of the openrc file has been tested
  and is known to contain all of the settings needed. Use others at your own
  risk. example: "source openrc"

### Openstack: Setup your private networks
Tenant networks can be created:
- Using Horizon 
- Using Heat 
- Using the neutron api. 

### Modify the Vagrantfile.example
1. Remove the ".example" suffix
2. Modify the site_config/example-* files as described below

### Create a Site_config directory and create a site-config file to describe your nodes
- The site_config directory should contain:
  - An environment configuration yaml file that must contain: (see the examples_site_config.yaml file)
	- Network ID:  ID of network to launch your VMs on.
	- Node data: To included
		- Node Name:
		- Private-IP:
		- Floating-IP:
		- Provisioning Scripts: 

  - An Openstack_image_file which contains the name of a valid openstack image in Glance.
    (see the example_openstack-image-name file) 
