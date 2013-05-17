Description
===========

Installs the Openstack dashboard (codename: Horizon) from packages.

http://horizon.openstack.org

Requirements
============

* Chef 0.10.0 or higher required (for Chef environment use).

Cookbooks
---------

The following cookbooks are dependencies:

* apache2
* database
* mysql / postgresql
* openstack-common >= 0.1.8

Usage
=====

db
--

Configures database for use with Horizon

```json
"run_list": [
    "recipe[openstack-dashboard::db]"
]
```


server
------

Sets up the Horizon dashboard within an Apache `mod_wsgi` container.

```json
"run_list": [
    "recipe[openstack-dashboard::server]"
]
```

Attributes
==========

* `openstack-dashboard["db"]["username"]` - username for horizon database access
* `openstack-dashboard["server_hostname"]` - sets the ServerName in the Apache config.
* `openstack-dashboard["use_ssl"]` - toggle for using ssl with dashboard (default true)
* `openstack-dashboard["ssl"]["dir"]` - directory where ssl certs are stored on this system
* `openstack-dashboard["ssl"]["cert"]` - name to use when creating the ssl certificate
* `openstack-dashboard["ssl"]["key"]` - name to use when creating the ssl key
* `openstack-dashboard["dash_path"]` - base path for dashboard files (document root)
* `openstack-dashboard["wsgi_path"]` - path for wsgi dir
* `openstack-dashboard["ssl_offload"]` - Set SECURE_PROXY_SSL_HEADER = ('HTTP_X_FORWARDED_PROTOCOL', 'https') flag for offloading SSL
* `openstack-dashboard["plugins"]` - Array of plugins to include via INSTALED\_APPS

Testing
=====

This cookbook is using [ChefSpec](https://github.com/acrmp/chefspec) for
testing. Run the following before commiting. It will run your tests,
and check for lint errors.

    $ ./run_tests.bash

License and Author
==================

Author:: Justin Shepherd (<justin.shepherd@rackspace.com>)
Author:: Jason Cannavale (<jason.cannavale@rackspace.com>)
Author:: Ron Pedde (<ron.pedde@rackspace.com>)
Author:: Joseph Breu (<joseph.breu@rackspace.com>)
Author:: William Kelly (<william.kelly@rackspace.com>)
Author:: Darren Birkett (<darren.birkett@rackspace.co.uk>)
Author:: Evan Callicoat (<evan.callicoat@rackspace.com>)
Author:: Jay Pipes (<jaypipes@att.com>)
Author:: John Dewey (<jdewey@att.com>)

Copyright 2012, Rackspace US, Inc.
Copyright 2012-2013, AT&T Services, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and⋅
limitations under the License.
