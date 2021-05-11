Ansible                 
================

Create test environment in AWS with ELB, EC2 instance, docker and NGINX

Requirements (on host that executes modules):

python 3
awscli
boto - Ansible will connect to AWS using the boto SDK. So, we need to install the boto and boto3 packages. :

$ pip3 install boto boto3

create a file under our user home folder (~/.boto):

[Credentials]
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_EY=...

Firstly, you need to run playbook (ELB/site.yml) to create an instance:

$ ansible-playbook site.yml  --private-key /home/k/.ssh/my_private_key.pem

Where the "my_private_key.pem" is my private key.

After deploing EC2, you need to specify the address in the "hosts" file - [webserver] ext_ip_addr

Then you need to run playbook files from directory Docker_container: 

$ ansible-playbook docker-configure.yml

Generate ssh key:

$  ssh-keygen -f ./mycontainerkey

$ ansible-playbook docker-container.yml

$ ansible-playbook deploymyapp.yml

Now you open your browser can test the application is working or not.
