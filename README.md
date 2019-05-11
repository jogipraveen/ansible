# Provision Jenkins slaves using Ansible

Provision a VM using Ansible using Vagrant and VirtualBox locally on Mac PC.
Pre req:
```bash
Python 3.7.3
VirtualBox: 6.0.6
Vagrant: 2.2.4
Ansible: 2.7.10
```

### Test ansible playbook locally.
```bash
$ vagrant up
```

### Create EC2 instance
- Pre req to create EC2 instance on AWS
    ```bash
    awscli          1.16.155
    boto            2.49.0
    boto3           1.9.145
    ```
- Create an AMI and download the keypair.

- Create AWS boto file with access and secret keys.
    ```bash
    cat ~/.boto
    [Credentials]
    AWS_ACCESS_KEY_ID=<AWS_ACCESS_KEY_ID>
    AWS_SECRET_ACCESS_KEY=<AWS_SECRET_ACCESS_KEY>
    ```
Create AWS EC2 instance.
```bash
$ ansible-playbook -vv create_ec2_instance.yml -i inventory/aws/hosts
```

Install required packages on the EC2 instance
```bash
$ ansible-playbook -vv provision_jenkins_build_slave.yml -i inventory/aws/hosts -u ec2-user  --private-key=~/Downloads/new_key.pem
```
