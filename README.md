Role Name
=========

ec2-security-groups

Requirements
------------

As this module uses the ec2 group of modulies, the boto library is
required.

Role Variables
--------------

The variables you will be required to provide are as follows:
  - region
      The AWS region the VPC belongs to, e.g. eu-west-1
  - aws_security_groups:
      A dictionary of security groups to create. You can use group_name or
      cidr_ip for the firewall rule; the group_name can already exist or
      be one you are creating with this role.
      Dictionary variable layout:
aws_security_groups:
  name:
    desc: some description here
    res_tags:
      name: value
      name2: value2
    rules:
      - proto: tcp / udp
        from_port: port #
        to_port: port #
        cidr_ip: IP range
      - proto: tcp / udp
        from_port: port #
        to_port: port #
        group_name: some-group-name

  - vpc_name
      The name of the VPC that the security groups will be created for.
      If your VPC does not have a name, you can pass in the vpc_id instead

Dependencies
------------

No external dependencies on other roles

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

GPLv3

Author Information
------------------

Iain M Conochie <iain.conochie@nttdata.com>
