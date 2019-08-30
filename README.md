
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

# run the playbook
ansible-playbook -i hosts playbook.yml

# run the playbook with vault pass and time it
time ansible-playbook -i hosts playbook.yml --ask-vault-pass
