Role Name
=========

Role to create a sealed secret deployment on a kubernetes cluster



Role Variables
--------------

```
CLUSTER_NAME
KUBECONFIG
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
REGION
CONFIG_MAP_AWS_AUTH
ACCOUNT_ID
```

Example Playbook
----------------


```
- hosts: "{{ lookup('env','BASTION_IP') }}"
  become: no
  remote_user: "ubuntu"

# Uncomment "aws-eks-setup" role only if you are upgrading the cluster
  roles:
    - role: aws-eks-setup
      BASTION_IP: "{{ lookup('env', 'BASTION_IP') }}"
      AWS_ACCESS_KEY_ID: "{{ lookup('env', 'AWS_ACCESS_KEY_ID') }}"
      AWS_SECRET_ACCESS_KEY: "{{ lookup('env', 'AWS_SECRET_ACCESS_KEY') }}"
      REGION: "{{ lookup('env', 'REGION') }}"
      CLUSTER_NAME: "{{ lookup('env', 'CLUSTER_NAME') }}"
      ROUTE_53_ARN: "{{ lookup('env', 'ROUTE_53_ARN') }}"
      KUBECONFIG: "{{ lookup('env', 'KUBECONFIG') }}"
      CONFIG_MAP_AWS_AUTH: "{{ lookup('env', 'CONFIG_MAP_AWS_AUTH') }}"
      ACCOUNT_ID: "{{ lookup('env', 'ACCOUNT_ID') }}"

```

License
-------

BSD

Author Information
------------------

- [César vergara](mailto:cvergarae@smu.cl)