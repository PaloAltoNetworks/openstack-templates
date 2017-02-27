Files:

init-cfg.ext
bootstrap.xml
--------------------
PAN firewall bootstrap files to bootstrap PAN firewall when deployed through HEAT.

pan_basic_gw_env.yaml
--------
Example HEAT template environment file.

pan_basic_gw.yaml
--------
Example HEAT template to deploy a PAN virtual firewall and Linux server instances.

This template expects following existing resources:
  - PAN image
  - Server image
  - Server key
  - Management network
  - Public network 

This template creates following resources:
  - Private network/subnets
  - Security group 
  - PAN virtual firewall instance
  - Linux server instance


