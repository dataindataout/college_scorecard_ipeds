# College Scorecard IPEDS data

This code downloads the College Scorecard dataset, extracts the IPEDS data, and loads it into tables in a 3-node YugabyteDB cluster.

## Local provisioning

Ansible is used to provision database clusters. 

To provisioning a test cluster and load the data, issue the following:
`ansible-playbook -i inventory.yml tasks/college-scorecard.yml`

## Notes about the College Scorecard IPEDS dataset

IPEDS = Integrated Postsecondary Education Data System

See <https://collegescorecard.ed.gov/assets/InstitutionDataDocumentation.pdf> for the official College Scorecard documentation about the institutional data.

## Prerequisites

- a copy of yugabytedb (see <https://download.yugabyte.com> for one option)
- set the group_vars yb_executable_dir to point to your desired YugabyteDB version
- set your path to include the bin and postgres/bin folders within your desired YugabyteDB version
- use set_ips.sh to set local ips for 6 nodes via set_ips.sh (127.0.01 - 127.0.0.3)
- add public ssh key to ~/.ssh/authorized_users file and ssh-add it

## Decommissioning cluster

- To decommission the cluster and remove data, issue the decomm.sh script.