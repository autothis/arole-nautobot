arole-nautobot
=========

Everything ansible nautobot related in one place

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Input Variables
General
- "{{ nautobot_url }}"
- "{{ nautobot_token }}"

Tenant's
- "{{ ClientCode }}" - Tenant name (could be short or full)
- "{{ ClientDescription }}" - Full Tenant name or description

VM's
- "{{ vm_name }}"
- "{{ vm_tag }}"
- "{{ DataCentre }}"
- "{{ dc.cluster }}"
- "{{ vm-size.cpu }}"
- "{{ vm-size.memory }}"
- "{{ vm-size.disk1-size }}"

VM Interfaces
- "{{ vm_name }}"
- "{{ vm_name.interface1 }}"
- "{{ vm_name.interface1.mode }}"
- "{{ vlan_name }}"
- "{{ DataCentre }}"

Regiser values - used for display during or after automation to supply as built documentation
- nb_tenant - documentation
- vm_result - exsists or not 


Lookup Variables
- {{ nb_device_role }} - Device role (slug) in Nautobot

Environmental Variables
- <db_password>
- <napalm_username>
- <napalm_password>
- <redis_password>
- <pgppassword>
- <psql_password>
- <superuser_email>
- <superuser_password>
- <superuser_token>
- <ldap_uri>
- <ldap_bind_dn>
- <ldap_bind_password>
- <nautobot_secret_key>
- <nautobot_allowed_hosts>

Look up
nautobot_url
nautobot_token
nautobot_VM_role


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

GNU GPLv32

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
