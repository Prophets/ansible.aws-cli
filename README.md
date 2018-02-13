# AWS CLI role for Ansible

Installs and configures the AWS CLI using PIP virtualenv.

Multiple AWS credentials can be set per profile, though currently only one profile configuration is allowed. Feel free to send merge requests.

## Requirements

Tested on Ubuntu 16.04 Server.

## Role Variables

The AWS CLI is installed by default for the remote user running the playbook.

    aws_cli_user: "{{ ansible_user | default(lookup('pipe', 'whoami')) }}"
    aws_cli_user_home_dir: "/home/{{ aws_cli_user }}"

The default AWS CLI related variables:

    aws_output_format: json
    aws_region: eu-central-1
    aws_profiles:
      - name: default
        key_id: YOUR_ACCESS_KEY_ID
        key_secret: YOUR_SECRET_ACCESS_KEY

## Example Playbook

    - hosts: servers
      roles:
        - role: prophets.aws-cli
          aws_output_format: json
          aws_region: eu-central-1
          aws_profiles:
            - name: default
              key_id: YOUR_ACCESS_KEY_ID
              key_secret: YOUR_SECRET_ACCESS_KEY

# License

This playbook is provided 'as-is' under the conditions of the BSD/MIT license. No fitness for purpose is guaranteed or implied.