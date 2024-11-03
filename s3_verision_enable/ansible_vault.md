create ssm parameter store with parameters as access_key and secret_key

In ansible control plane

 ansible-vault view group_vars/all/pass.yml --vault-password-file vault.pass


aws_access:  "{{ lookup('amazon.aws.aws_ssm', 'access_key', region='us-east-1') }}"
aws_secret:  "{{ lookup('amazon.aws.aws_ssm', 'secret_key', region='us-east-1') }}"
