## v0.6.0
* Switched to OpenStack API from OpenStack EC2 API.
* Updated to point to master branch of Fog for latest `OpenStack` provider
* testing with Diablo & Essex
* knife openstack server create (KNIFE_OPENSTACK-1)
* knife openstack server delete (KNIFE_OPENSTACK-2)
* Support for unenven_columns for prettier output (KNIFE_OPENSTACK-5)
* Added chef gem dependency (KNIFE_OPENSTACK-6)
* Added virtual cpus to 'knife openstack flavor list'
* Removed unsupported features to match current state of plugin (public_key, kernel, architecture, cores, location)
* Added support for openstack_tenant (Rob Hirschfeld & Alexander Gordeev)
* Server list supports many more states
* Added support for associating floating IPs on server create and verified they are automatically disassociated on server delete
* Added /etc/chef/ohai/hints/openstack.json file with server.addresses since floating IPs are not available from the node. Bootstrap templates are geting updated and Ohai plugin will read it.

## v0.5.2
* initial Cactus release using EC2 API

# BACKLOG/ISSUES #

This is a list of features currently lacking and (eventually) under development:

* node still has wrong public ip address with associated floating IPs
* purge only works when names match up with clients
* not blow up when it gets an empty public ip address on server create
* `knife openstack floating list|associate|disassociate ip|node`
* need an ohai plugin to populate `cloud` and `openstack` attributes
* fix support for not using `-S`, by listing it in the knife.rb instead
* automate naming of nodes if `--node-name` is not passed
* take either the flavor ID or the flavor name
* take either the image ID or the image name
* add `-G` support for security groups other than 'default'
* more information in `knife openstack image list`
* get DNS names working
* availability zones
* filter out the *-initrd and *-kernel from 'openstack image list'. Fog -> container_format={aki|ari} or disk_format on the same params
* assumption of only single floating IP (and fog uses the last as the public_ip_address)