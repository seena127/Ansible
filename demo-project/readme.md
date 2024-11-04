#first create vault.pass file to store aws secret key and access key

create password for vault

openssl rand -base64 2048 > vault.pass

Add your AWS credentials using the below vault command

ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass

now add
access_key:
secret_key:
save it

install boto3 and python interpreter

project tasks:

1)task 1:

create aws resource using ansible using loops of different os families

2)task 2:


create password less authentication for all the created ec2 instance make sure there is open port 22

ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>

3) task 3:

shutdown all instances that doesnot belong to specific os family

create inventory file with ip address of the created resources inside it ec2.ini

ansible-playbook ec2_stop.yml -i ec2.ini --vault-password-file vault.pass

4) Ansible vault can be integrated with parameter store by changing ansible vault as

ansible-vault view group_vars/all/pass.yml --vault-password-file vault.pass


aws_access:  "{{ lookup('amazon.aws.aws_ssm', 'access_key', region='us-east-1') }}"

aws_secret:  "{{ lookup('amazon.aws.aws_ssm', 'secret_key', region='us-east-1') }}"

Make sure the user has necessary permissions
