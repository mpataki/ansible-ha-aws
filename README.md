# ansible-ha-aws

This ansible roles installs the aws-cli as well as your aws config and credentials so other systems can use them.

## Requirements

Really this should work on any debian based system, but has been tested on a Raspberry Pi running Hassbian.

## Role Variables

- `aws_default_region`
  - Ex. `us-east-1`
  - This is the default AWS region that any actions you take with the cli will be performed against.
- `aws_credentials`
  - This is a list of objects with keys `name`, `aws_access_key_id`, and `aws_secret_access_key` representing your credentials.
  - Ex:

```yaml
aws_credentials:
  - name: default
    aws_access_key_id: <your-access-key-id>
    aws_secret_access_key: <your-secret-access-key>
  - name: s3-access
    aws_access_key_id: <your-access-key-id-2>
    aws_secret_access_key: <your-secret-access-key-2>
```

## Dependencies

You first need to sign up for an AWS account and create some credentials.

## Example Playbook

```yml
    - hosts: pi
      vars:
        aws_credentials:
          - name: default
            aws_access_key_id: <your-access-key-id>
            aws_secret_access_key: <your-secret-access-key>
          - name: s3-access
            aws_access_key_id: <your-access-key-id-2>
            aws_secret_access_key: <your-secret-access-key-2>
      roles:
         - role: mpataki.ha-aws
```

## License

MIT
