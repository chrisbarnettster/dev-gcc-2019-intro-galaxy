
based on https://galaxyproject.github.io/training-material/topics/admin/tutorials/ansible-galaxy/tutorial.html

# make sure ansible is a recent version 


```
# from a playbook
ansible-playbook -i hosts ansible-update.yml

# or manually if you must
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible -y
```
# install roles
ansible-galaxy install -p roles -r requirements.yml

# mount some ceph storage
time ansible-playbook -i hosts mount-ceph-playbook.yml --ask-vault-pass

# run the playbook
ansible-playbook -i hosts playbook.yml

# run the playbook with vault pass and time it
time ansible-playbook -i hosts playbook.yml --ask-vault-pass


# Appendix

## perms updates
playbook perms are not working for me. Should add a post perms update or something. For now here is what works
Need confidential data but also web service must work
used `su -s /bin/bash www-data` to check where web user has perms

```
cd /path/to/galaxy
sudo chown -R galaxy.galaxy config/
sudo chown -R galaxy.galaxy local_tools
sudo chown -R galaxy.galaxy server
sudo chown -R galaxy.galaxy venv
sudo chown galaxy.galaxy ../galaxy
sudo chmod o+rx ../galaxy
sudo chmod +rx server
```
