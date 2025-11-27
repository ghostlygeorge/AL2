This project builds a CIS-hardened Amazon Linux 2 AMI using Packer and Ansible.
All you need to do is export AWS credentials and run the build script.

Usage
1. Export AWS credentials
export AWS_ACCESS_KEY_ID="your_key"
export AWS_SECRET_ACCESS_KEY="your_secret"
export AWS_DEFAULT_REGION="eu-west-1"


Or use a profile:

export AWS_PROFILE="your-profile"

2. Build the AMI
./ksac-packer-build.sh


Packer launches a temporary EC2 instance, applies Ansible CIS hardening, and outputs a secure AMI.

Repository Structure
.
├── ksac-packer-build.sh
├── ksac-packer.json
├── playbook.yml
└── roles/amazon_linux_cis_hardening/
    ├── tasks/ (CIS sections)
    ├── files/ (audit.rules, banner, sshd_config)
    ├── defaults/
    ├── vars/
    └── handlers/

Customization

Modify hardening rules under:

roles/amazon_linux_cis_hardening/tasks/


Adjust variables in:

roles/amazon_linux_cis_hardening/defaults/main.yml

Output

After completion, Packer prints the AMI ID:

AMI created: ami-xxxxxxxxxxxx
