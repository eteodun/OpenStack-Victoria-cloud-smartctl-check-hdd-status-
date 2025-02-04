# OpenStack-Victoria cloud smartctl check hdd status
Check HDD status cloud computes on openstack Victoria

# Description
This ansible script is dedicated to check status of HDD disk with smartmontools on cloud computes and generate logs in case that are found issues

Can be used and has been tested on Openstack Victoria


## Setup and instalation

Create file inventory.ini and populate with compute hostnames from /etc/hosts and place on ansible folder for eg: /var/lib/cee/main/system/Cloud_1/orchestrator/ansible/


Eg: hostnames
[compute_nodes]
compute-0-10
compute-0-11
compute-0-12
compute-0-14
....

## Install smartmontools on each compute
Copy file installsmart to one of cloud controller 

ceeinfra@infra1:~> chmod +x installsmart

ceeinfra@infra1:~>./installsmart

ceeinfra@infra1:~> sudo mkdir /var/log/smartcl

ceeinfra@infra1:~> sudo chown -R ceeinfra:ceeinfra /var/log/smartcl

Copy smartctl.yml to /var/lib/cee/main/system/Cloud_1/orchestrator/ansible/


## Run script 
ansible-playbook -i /var/lib/cee/main/system/Cloud_1/orchestrator/ansible/inventory.ini /var/lib/cee/main/system/Cloud_1/orchestrator/ansible/smartctl.yml

## Results 
Expected result 


PLAY RECAP ******************************************************************************************************************************************
compute-0-10               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-11               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-13               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-14               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-15               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-16               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-17               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-18               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-20               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=1  << Has only 1 disk 
compute-0-21               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0
compute-0-22               : ok=2    changed=1    unreachable=0    failed=0    skipped=3    rescued=0    ignored=1  << Has only 1 disk 
