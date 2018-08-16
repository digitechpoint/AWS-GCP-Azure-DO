## How to Enable SSH Password Authentication

Some server providers, such as Amazon EC2 and Google Compute Engine, disable SSH password authentication by default. That is, you can only log in over SSH using public key authentication.

To enable SSH password authentication, you must SSH in as root to edit this file. Then, change the line

```
sudo nano /etc/ssh/sshd_config
```

Then, change the line

```
PasswordAuthentication no
```

to

```
PasswordAuthentication yes
```

After making that change, restart the SSH service by running the following command as root:

```
sudo service ssh restart
```

## Enable Logging In as root

Some providers also disable the ability to SSH in directly as root. In those cases, they created a different user for you that has sudo privileges (often named ubuntu). With that user, you can get a root shell by running the command:

```
sudo -i
```

If you instead want to be able to directly SSH in as root, again edit this file:

```
/etc/ssh/sshd_config
```

And change the line

```
PermitRootLogin no
```

to

```
PermitRootLogin yes
```

After making that change, restart the SSH service by running the following command as root:

```
sudo service ssh restart
```

If you enable this setting, don't forget to set a strong password for root by running the command.

```
sudo passwd root
```
