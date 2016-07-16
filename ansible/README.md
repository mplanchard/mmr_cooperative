# Infrastructure with Ansible

[Ansible][ansible] is an infrastructure-provisioning framework written
in Python. While Ansible is open-source, the project is owned and run
by RedHat, the company that makes RedHat Enterprise Linux. Please
review the linked documentation for more information on how to work
with Ansible.

[ansible]: http://docs.ansible.com/ansible/index.html "Ansible"

## installation

Although some things with ansible are slightly more complicated in a 
virtual environment, particularly dynamic environments (which we are
not using at the moment) I recommend installing it into a python
virtual environment. If you're on a Mac, you've already got Python 2.7
installed (ansible does not yet support Python 3), so you should be 
able to run the following (run from the root directory of this
repository):

```bash
sudo pip2.7 install --upgrade virtualenv
virtualenv -p python2.7 venv  # Create the virtual environment
source venv/bin/activate  # Activate the virtual environment
pip install ansible
```

## Inventory

The inventory directory contains an inventory file (`inventory.yml`),
which contains information about the host to which we will be
connecting when running ansible playbooks. Because the DNS name is
currently a huge garble, we are assigning the host to the "main"
group. We can set variables on the main group in the file 
`inventory/group_vars/main.yml`.

## Rles

Roles are customizable units of functinoality. I don't have 
documentation written for all of the roles yet, but it is coming.

## Deployment

The `deploy.yml` playbook will deploy the roles specified therein to
the webserver. To run a deployment, ensure you have activated your
virtual environment (see [Installation](#Installation)), and then run:

```bash
ansible-playbook -u <username> -i inventory deploy.yml
```
