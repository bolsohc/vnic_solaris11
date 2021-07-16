Role Name
=========

This role will use the ipadm_addr module to create new ipmp groups and vnics and apply the public IP addressed to them


Role Variables
--------------

VARS are configured in vars/main.yml. Add, or modify there if you need to change the public IP address or the hosts involved.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

# cat addpublicip.yml 
---

- hosts: hostname



  tasks:

      - import_role:
           name: vnic_solaris11 


      - name: show changes
        shell: ipadm
        register: result
        tags: deploy, rollback

      - debug: var=result.stdout_lines
        tags: deploy, rollback

To add new addres: 
   # ansible-playbook addpublicip.yml --deploy

To remove the new address:
   # ansible-playbook addpublicip.yml --rollback


Author Information
------------------

ispinosa 15-Nov-2019
