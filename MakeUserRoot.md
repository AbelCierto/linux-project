# Jenkins User Setup Commands

This documentation provides step-by-step commands to create and configure a Jenkins user with sudo privileges on Linux systems.

## Create Jenkins User

Create a new user account for Jenkins:

```bash
sudo adduser jenkins
```

## Add Jenkins to Wheel Group

Add the Jenkins user to the wheel group (or sudo group on Ubuntu/Debian systems):

```bash
sudo usermod -aG wheel jenkins
```

**Note:** On Ubuntu/Debian systems, use `sudo` group instead:
```bash
sudo usermod -aG sudo jenkins
```

## Configure Passwordless Sudo

Grant Jenkins user passwordless sudo access by creating a sudoers configuration file:

```bash
echo 'jenkins ALL=(ALL) NOPASSWD:ALL' | sudo tee /etc/sudoers.d/jenkins
```

## Disable TTY Requirement

Allow Jenkins to run sudo commands without a TTY (useful for automated processes):

```bash
echo 'Defaults:jenkins !requiretty' | sudo tee -a /etc/sudoers.d/jenkins
```

## Set Proper Permissions

Set the correct permissions on the sudoers configuration file:

```bash
sudo chmod 440 /etc/sudoers.d/jenkins
```

## Verify Configuration

Test that the passwordless sudo configuration is working correctly:

```bash
sudo -n true && echo "NOPASSWD OK"
```

If the configuration is correct, you should see "NOPASSWD OK" as output.

## Security Considerations

- The `NOPASSWD:ALL` configuration grants the Jenkins user full sudo access without password verification
- This setup is typically used for CI/CD automation where password prompts would interrupt automated processes
- Consider restricting sudo access to specific commands if enhanced security is required
- Regularly audit the Jenkins user's activities and permissions

## Troubleshooting

If the verification command fails:
1. Check the syntax of `/etc/sudoers.d/jenkins`
2. Verify file permissions are set to 440
3. Ensure the Jenkins user exists and is in the appropriate group
4. Test sudo access by switching to the Jenkins user: `sudo -u jenkins sudo whoami`