# AWX install and usage

## install AWX version using tar.gz file
```shell
sudo yum install git wget
wget https://github.com/ansible/awx/archive/17.1.0.tar.gz
tar -zxvf 17.1.0.tar.gz
cd awx-17.1.0
cd installer
```
## Setup the python virtualenv suitable for selinux Centos 7  
```shell
sudo yum -y install python3-virtualenv  # install selinux package for python3
sudo yum -y install python-virtualenv   # install selinux package for python2
sudo yum -y install libselinux-python3  # install bindings selinux with python3
virtualenv --system-site-packages venv-system # virtual on system-packages not local to the directory
source venv-system/bin/activate  # activate the virtual env 
sudo python3 -m pip install -U pip
sudo pip3 install wheel   # install wheel permissions
sudo pip3 install ansible
sudo pip3 install docker   # library python pour ansible
sudo pip3 install docker-compose # pour les containers d'AWX
```
# Add credentials file 
```shell
vi vars.yml
# add these lines
admin_password: 'adminpass'
pg_password: 'pgpass'
secret_key: 'mysupersecret'
do Esc , : wq
ansible-playbook -i inventory install.yml -e @vars.yml
```

## AWX Tutorial
Create a user  
Create a team  
Create credentials, source control  
and Machine, copy your private ssh key    
Create a projet  
Create an inventory  
Create a Job Template  
Execute the Job Template  


