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
  - vpc_name
      The name of the VPC that the security groups will be created for.
      If your VPC does not have a name, you can pass in the vpc_id instead
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

Dependencies
------------

No external dependencies on other roles

Example Playbook
----------------

    - hosts: localhost
      vars: 
        - region: eu-west-1
          vpc_name: Management
          aws_security_groups:
            allow_ssh:
              desc: Allow ssh to public interface
              res_tags:
                VPC: "{{ vpc_name }}"
                Name: Allow public SSH
              rules:
                - proto: tcp
                  from_port: 22
                  to_port: 22
                  cidr_ip: 0.0.0.0/0
      roles:
         - ec2-security-groups

License
-------

GPLv3

Author Information
------------------

Iain M Conochie <iain@shihad.org>
