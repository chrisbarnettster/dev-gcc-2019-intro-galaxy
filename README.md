
based on https://galaxyproject.github.io/training-material/topics/admin/tutorials/ansible-galaxy/tutorial.html
# install roles
ansible-galaxy install -p roles -r requirements.yml

# run the playbook
ansible-playbook -i hosts playbook.yml
