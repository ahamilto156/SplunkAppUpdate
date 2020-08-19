# SplunkAppUpdate - README
## Introduction
Ansible playbooks to update an application that resides on the deployment server

## GIT
cd ${BaseDir}

git clone https://github.com/ahamilto156/SplunkAppUpdate.git

## Requirements
For any required Ansible roles, review:
[requirements.yml](requirements.yml)

## Hosts file
cd  .../SplunkAppUpdate

sed -i s/"{{ Local_FQDN }}"/${Your_DomainName} hosts

vim hosts ###for hosts configuration

##  Variables
[vars/single_apps_vars.yml](vars/single_apps_vars.yml)

## Roles
cd  .../SplunkAppUpdate

./initialiseRepo.sh

### NOTE
- ATM not needed as there are no roles to load. It is in there for consistancy's sake and to make it easier if roles are ever introduced into this playbook

## Execution
1/ Run the Get App playbook

ansible-playbook -kK get_app_from_deployer.yml --ask-vault-pass \

    -e sapp_name=${Application_Name}[,sapp_edit_path=${LocnTheAppIsToBeEditedFrom}]
    
2/ Edit the application;

3/ Run the Get App playbook

ansible-playbook -kK put_app_via_deployer.yml --ask-vault-pass \

    -e sapp_name=${Application_Name}[,sapp_edit_path=${LocnTheAppIsToBeEditedFrom}]
    
### NB
The above method assumes [despite what assuming does] that the apps tree is populated.

... If not, then the reloading of the deployment server will uninstall ${Application_Name}

### NOTES

1/ ${TheLocationYouWant TheAppToBeModifiedFrom} = The directory where you wish to edit the application from 

    e.g. /home/${developer}/splunk_apps/${app_name}
2/ sapp.type = 

    a)          "local" => whether it is a local app that is not to be deployed to ALL search heads
    
    b)          "shared" (default) => whether it is a shared app that is  to be deployed to ALL search heads that the deployment server
                 knows about

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
      I would like to thank everyone that created roles that I plagiarise and/or use.
