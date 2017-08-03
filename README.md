ansible-hacluster
=========

Role to create a two node ha cluster using pcs, pacemaker and corosync.

Requirements
------------

Code is partially tested in RHEL 7 and Debian specific code is under development.
Tasks for creating fencing device is in virtfence.yml should be considered as a hint and please make necessary changes. It is under testing and unsafe code is commented out.

Role Variables
--------------

Follwing variables in defaults/main.yml should be set to your environment

	hacluster_password: Change_Me
	pcs_cluster1: set_an_ip1
	pcs_cluster2: set_an_ip2
	cluster_name: set_name
	virt_fencing: false
	ip_of_esxi: set_esxi_or_vcenter_ip
	sxi_username: set_esxi_or_vcenter_username
	sxi_password: set_esxi_or_vcenter_password

Tasks under virtfence.yml is disabled when virt_fencing is set to false.

Dependencies
------------

As of now no dependency. However I have plans to fork fencing code to separate role.

Example Playbook
----------------

Example playbook to try this role
---
- hosts: ['node1','node2']
  become: true
  remote_user: vagrant
  roles:
    - { role: ansible-hacluster, pcs_cluster1: node1, pcs_cluster2: node2, create_cluster: mycluster }

License
-------

BSD

Author Information
------------------
Chanchal Bose 
Company: Prodevans LLC
Githup repo: https://github.com/chanchalbose
Docker repo: https://hub.docker.com/r/chanchal
YouTube Channel: mostlylinux


