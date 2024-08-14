# Access control and user authentication

To restrict which user can perform changes to the system state you can activate access control by creating user accounts.
If no user accounts exist on a machine then access control is disabled.

## Supported user roles

The following roles are currently checked:

- read-write
  - Allows modifying most of the system state except network configuration

- net-admin
  - Allows modifying the network configuration like IP addresses

## Creating user accounts

To create a user account connect to the machine via SSH or using the serial console and execute the following command:

`$ vm-adduser USERNAME [ROLE ROLE ...]`

When no roles are set for a user, then that user has read only access

### Creating a super user account

It is also possible to create a super user account:

`$ vm-adduser USERNAME --all`

## HTTPS login and default access

Once user accounts exist all access to the machine requires a HTTPS basic auth login (the logged in user is stored in the session).

It is possible to allow access without login by enabling a default access:

`$ vm-adduser --default [ROLE ROLE ...]`

When no roles are specified the default is read only access

## Deleting user accounts

To delete an user account or default setting you can use the following command:

```bash
$ vm-deluser --default
$ vm-deluser USERNAME
```

## Preventing SSH login using the default password

To prevent someone from accessing the machine via SSH using the default password you should disable password based SSH authentication:

`$ disable_ssh_password.sh`

This tool will update the sshd configuration file to only access public key based authentication (it will warn when no authorized keys are installed). You need to reboot after making this change.

Password based login via the serial console will still be possible.