Role Name
=========

Installs ElasticSearch from either a local file of the yum-local repository. If the yum-local repository is not availble, playbook will look for installers in the /files/installers location, where it will copy to and install from on remote servers as defined in the play.

Requirements
------------

ElasticSearch requires JDK 8.1.131 installed and port 9200 accessible. 

Role Variables
--------------

You must provide the following:

```
es_node_name: Contains the name of the node elasticsearch is being installed to.
es_zen_hosts: Contains array of hosts in the elasticsearch cluster, examples - [ "default-node1","defaults-node2" ]  
es_watcher_email: Email address that watcher will send emails from.
es_bind_password: Password to user that has ldap read access (Default svc_elasticsrch)
```

The following are the remaining variable options. They all have default values for test environments. 

```
es_master:
es_data:
es_datapath:

es_bootstrap_system_call_filter: "false"
es_bootstrap_memory_lock: "true"

es_network_host: 0.0.0.0
es_http_port: 9200
es_min_master_nodes: 1

es_gateway_expected_nodes: 1
es_recover_after_time: 120m
es_recover_after_nodes: 1

es_smtp_host: mail5.uhc.com
es_smtp_port: 25

es_xms: 512m
es_xmx: 512m
```

es_rpm: elasticsearch-5.4.1.rpm
es: elasticsearch-5.4.1
repo: artifactory-yum-local

es_plugins:
  - plugin_name: "file:///tmp/x-pack-5.4.1.zip --batch"

es_cluster_name: default

es_node_name: default-node1
es_master: "true"
es_data: "true"
es_datapath: /var/lib/elasticsearch

es_bootstrap_system_call_filter: "false"
es_bootstrap_memory_lock: "true"

es_network_host: 0.0.0.0
es_http_port: 9200
es_zen_hosts: |-
  ["default-node1"]
es_min_master_nodes: 1

es_gateway_expected_nodes: 1
es_recover_after_time: 120m
es_recover_after_nodes: 1

es_watcher_email: |-
  es-Default@optum.com
es_smtp_host: mail5.uhc.com
es_smtp_port: 25

es_ad_domain: ms.ds.uhc.com
es_ldap_url: |-
  ldap://ad-ldap-prod-elr.uhc.com:389
es_bind_dn: |-
  CN=svc_elasticsrch,CN=Users,DC=ms,DC=ds,DC=uhc,DC=com
es_bind_password: changeme

#Java and CPU settings
es_xms: 512m
es_xmx: 512m


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
es_xms: 512m
es_xmx: 512m
    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

