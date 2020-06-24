# SplunkAppUpdate - README
Ansible playbooks to update an application that resides on the deployment server

## GIT
cd ${BaseDir}

git clone https://github.com/ahamilto156/SplunkAppUpdate.git

## Requirements
For any required Ansible roles, review:
[requirements.yml](requirements.yml)

## Hosts file
cd  .../SplunkAppUpdate

cp hosts_template.yml hosts

sed -i s/"{{ Local_FQDN }}"/${Your_DomainName} hosts

vim hosts ###for hosts configuration

##  Variables
[defaults/main.yml](defaults/main.yml)

cd  .../SplunkAppUpdate
./initialiseRepo.sh

## Method
ansible-playbook -kK get_app_from_deployer.yml -e ${Application_Name}[,local]
Edit the application
ansible-playbook -kK put_app_to_deployer.yml -e ${Application_Name}[,local]


### NOTES:
1/ The local is if it is a local app that is not to be deployed to ALL search heads

## License
Free

# Author Information
Andrew Hamilton MEngSc. (Elec.), Grad Dip. PM, BE (Comp.)

Senior Consultant
Red Hat

A: L11, 40 Marcus Clarke Street,
    Canberra City, ACT, 2601, Australia

E: andrew.hamilton@redhat.com  

M: +61-477-242-645-[+61-477-ahamil]

F: +61-2-6247-4380    

# Acknowledgements
- Firstly:
      I would like to thank Geoff Gatward [GG] who patiently taught me much of what I know about Ansible
- Secondly:
      I would like to thank everyone that created roles that I utilise. These roles are listed in [roles/requirements.yml](roles/requirements.yml) 