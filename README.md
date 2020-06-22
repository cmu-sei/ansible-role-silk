SiLK
=========

SiLK, the System for Internet-Level Knowledge, is a collection of traffic analysis tools developed by the [CERT Network Situational Awareness Team](www.cert.org/netsa) (CERT NetSA) to facilitate security analysis of large networks. The SiLK tool suite supports the efficient collection, storage, and analysis of network flow data, enabling network security analysts to rapidly query large historical traffic data sets. SiLK is ideally suited for analyzing traffic on the backbone or border of a large, distributed enterprise or mid-sized ISP.

A SiLK installation consists of two categories of applications: the packing system and the analysis suite. The packing system collects IPFIX, NetFlow v9, or NetFlow v5 and converts the data into a more space efficient format, recording the packed records into service-specific binary flat files. The analysis suite consists of tools which read these flat files and perform various query operations, ranging from per-record filtering to statistical analysis of groups of records. The analysis tools interoperate using pipes, allowing a user to develop a relatively sophisticated query from a simple beginning.

Role Variables
--------------

Available variables are listed below, along with default values (see [defaults/main.yml](defaults/main.yml)):

	silk_version

The version of silk to install. The master branch will always point to the latest available version.

	netsa_url: "http://tools.netsa.cert.org/releases/"
	silk_name: "silk-{{ silk_version }}"
	silk_tgz: "{{ silk_name }}.tar.gz"
	silk_url: "{{ netsa_url }}{{ silk_tgz }}"
	silk_timeout: 10
	silk_checksums:
	  '3.19.1': sha256:b287de07502c53d51e9ccdcc17a46d8a4d7a59db9e5ae7add7b82458a9da45a7
	  '3.19.0': sha256:0f5bdcf437a1dc0429a5acb48b8e9ef18050999a230920369c05b2db9f020695
	  '3.18.3': sha256:25fc734d6cac7d39285877ff5efd78bd4e5bb34523a6c4f6174afc9e2a87c2a2
	  '3.18.2': sha256:855ce1ce862fc2cb7146a04cbe60ba2584ff7df176e07494a2f14d26976b4c2b
	  '3.18.1': sha256:0900a5a0d08c786be280d97e5bb6d9ec09e8aec69f4495a91b32e254014ef8e9	
	silk_checksum: '{{ silk_checksums[silk_version] }}'

Helper variables used to download the silk release from the [netsa tools site](https://tools/netsa.cert.org).

Dependencies
------------

- cmusei.fixbuf

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: cmusei.silk
           tags: ['silk']

License
-------

Copyright 2020 Carnegie Mellon University.
NO WARRANTY. THIS CARNEGIE MELLON UNIVERSITY AND SOFTWARE ENGINEERING INSTITUTE MATERIAL IS FURNISHED ON AN "AS-IS" BASIS. CARNEGIE MELLON UNIVERSITY MAKES NO WARRANTIES OF ANY KIND, EITHER EXPRESSED OR IMPLIED, AS TO ANY MATTER INCLUDING, BUT NOT LIMITED TO, WARRANTY OF FITNESS FOR PURPOSE OR MERCHANTABILITY, EXCLUSIVITY, OR RESULTS OBTAINED FROM USE OF THE MATERIAL. CARNEGIE MELLON UNIVERSITY DOES NOT MAKE ANY WARRANTY OF ANY KIND WITH RESPECT TO FREEDOM FROM PATENT, TRADEMARK, OR COPYRIGHT INFRINGEMENT.
Released under a MIT (SEI)-style license, please see license.txt or contact permission@sei.cmu.edu for full terms.
[DISTRIBUTION STATEMENT A] This material has been approved for public release and unlimited distribution.  Please see Copyright notice for non-US Government use and distribution.
CERT® is registered in the U.S. Patent and Trademark Office by Carnegie Mellon University.
This Software includes and/or makes use of the following Third-Party Software subject to its own license:
1. ansible (https://github.com/ansible/ansible/tree/devel/licenses) Copyright 2019 Red Hat, Inc.
2. molecule (https://github.com/ansible-community/molecule/blob/master/LICENSE) Copyright 2018 Red Hat, Inc.
3. testinfra (https://github.com/philpep/testinfra/blob/master/LICENSE) Copyright 2020 Philippe Pepiot.
DM20-0487

Author Information
------------------

This role was created in 2019 by [Matt Heckathorn](https://resources.sei.cmu.edu/library/author.cfm?authorID=2403).
