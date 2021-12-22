# Secure Shell \(SSH\)

* [OpenSSH Manual Pages](https://www.openssh.com/manual.html)

## Guides

* [OpenSSH Guidelines](https://infosec.mozilla.org/guidelines/openssh) \(Mozilla\)
* [Secure Secure Shell](https://stribika.github.io/2015/01/04/secure-secure-shell.html) - [stribika](https://twitter.com/stribika)
* [Securing SSH](https://wiki.centos.org/HowTos/Network/SecuringSSH) \(CentOS Wiki\)

## Articles

* [The default OpenSSH key encryption is worse than plaintext](https://latacora.singles/2018/08/03/the-default-openssh.html) \(Latacora Blog\)
* [ChaCha20 and Poly1305 in OpenSSH](http://blog.djm.net.au/2013/11/chacha20-and-poly1305-in-openssh.html)
* [How Facebook does SSH at scale](https://code.fb.com/security/scalable-and-secure-access-with-ssh/)

## Tools

* [ssh\_scan](https://github.com/mozilla/ssh_scan) “configuration and policy scanner” \(Mozilla\)
* [Secretive](https://github.com/maxgoedjen/secretive) Generate and store SSH keys in the Mac Secure Enclave (`ecdsa-sha2-nistp256` keys)

## Key Types

Key types are listed in the order of preference below:

* `ED25519`
* &gt;= 2048bit `RSA`
* `ECDSA`
  * `DSA` and `ECDSA` both [fail catastrophically on bad randomness](https://security.stackexchange.com/questions/5096/rsa-vs-dsa-for-ssh-authentication-keys/46781#46781).
  * **Never** use `DSA` keys 
  * Avoid `ECDSA` keys if you can

## Mobile

If you use SSH on the go often you'll want to look at using [Mosh](https://mosh.org/)

### iOS

* [Termius](https://www.termius.com/) [App Store](https://itunes.apple.com/us/app/termius-ssh-shell-console-terminal/id549039908?mt=8) \(free\)
* [Prompt 2](https://panic.com/prompt/) [App Store](https://itunes.apple.com/gb/app/prompt-2/id917437289?mt=8) \(£14.99\)

## Examples

### Generate Keys

The `ssh-keygen` utility is used to create new SSH keys on most \*nix systems.

#### ED25519

```text
ssh-keygen -t ed25519 -a 100
```

* `-t`: Type of key to generate
* `-a`: Number of Key Derivation Function \(KDF\) rounds

### Remove Hashed known\_hosts Entry

If your client is set to hash known hosts e.g. has the following line in `~/.ssh/config`

```text
HashKnownHosts yes
```

Then your `~/.ssh/known_hosts` file will be obfuscated.

To remove a host, when its hosts key changes, you'll need to execute:

```text
ssh-keygen -R example.com
```

Which will remove all keys associated with that hostname from `~/.ssh/known_hosts`.

## Configuration

### Client

#### Permissions

```text
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_*
chmod 644 ~/.ssh/id_*.pub
```

Only allow your user to access `~/.ssh` and your private keys, allow group and world to access your public keys.

#### config

```bash
  # ~/.shh/config 
  # ssh_config(5) 

  Host * 
  # For all hosts use the following directives 

  Protocol 2 
  # Use only protocol version two 

  IdentitiesOnly yes 
  # By default ssh will send all public keys (identities) in ~/.ssh to the server if you don't specify which key to use with -i 
  # This prevents that by only using the public keys explicitly configured in config or specified with -i 

  VisualHostKey yes 
  # Print an ASCII art representation of the remote host key fingerprint at login and for unknown host keys 

  HashKnownHosts yes 
  # Hash host names and addresses when they are added to ~/.ssh/known_hosts. 
  # ssh-keygen -R hostname 
  # Removes all keys belonging to hostname from a known_hosts file. 
  UseRoaming no 
  # Mitigates CVE-0216-0777 

  # Cryptography 

  KexAlgorithms curve25519-sha256
  # Allow only curve25519

  HostKeyAlgorithms ssh-ed25519,ecdsa-sha2-nistp256
  # Allow only ed25519 or ECDSA keys for client authentication
  # ECDSA for Secretive/ Secure Enclave keys
  # ed25519 for everything else

  Ciphers chacha20-poly1305@openssh.com
  # Only use chacha20-poly1305
  # Chacha20-poly1305 is preferred over AES-GCM because the SSH protocol does 
  #   not encrypt message sizes when GCM (or EtM) is in use. 
  #   This allows some traffic analysis even without decrypting the data.
  #   See: http://blog.djm.net.au/2013/11/chacha20-and-poly1305-in-openssh.html

  MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,umac-128-etm@openssh.com
  # Only use encrypt then mac (etm) MACs
  # Allow only HMAC-SHA2-512/256 or UMAC-128
  #   https://crypto.stackexchange.com/a/56432
```

### Server

#### Permissions

```text
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

Only allow your user to access `~/.ssh` and `~/.ssh/authorized_keys`. **These permissions are required** by the [`StrictModes`](https://man.openbsd.org/sshd_config#StrictModes) directive.

#### sshd\_config

```bash
# /etc/ssh/sshd_config 
# sshd_config(5) 

AddressFamily inet 
# Only use IPv4 

ListenAddress x.x.x.x 
# Default is to listen on all local addresses 
# Better to specify an actual IP address to listen on 

Protocol 2 
# Only use protocol version 2 

LogLevel VERBOSE 
# Logs user's key fingerprint on login 

HostKey /etc/ssh/ssh_host_ed25519_key
HostKey /etc/ssh/ssh_host_ecdsa_key
# Key files cannot be group/world-accessible 

PermitRootLogin no 
# root user cannot login via SSH 

AuthenticationMethods publickey 
# Only allow public key authentication for login 

Subsystem sftp internal-sftp 
# Use sshd internal SFTP server code (plays nicer with Chroot) 
# See https://serverfault.com/a/660325 for differences with 
# Subsystem sftp /usr/libexec/openssh/sftp-server 
# If you just scp files you can disable this to reduce attack surface 

# Cryptography 

KexAlgorithms curve25519-sha256
# Allow only curve25519

HostKeyAlgorithms ssh-ed25519,ecdsa-sha2-nistp256
# Allow only ed25519 or ECDSA keys for client authentication
# ECDSA for Secretive/ Secure Enclave keys
# ed25519 for everything else

Ciphers chacha20-poly1305@openssh.com
# Only use chacha20-poly1305
# Chacha20-poly1305 is preferred over AES-GCM because the SSH protocol does 
#   not encrypt message sizes when GCM (or EtM) is in use. 
#   This allows some traffic analysis even without decrypting the data.
#   See: http://blog.djm.net.au/2013/11/chacha20-and-poly1305-in-openssh.html

MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,umac-128-etm@openssh.com
# Only use encrypt then mac (etm) MACs
# Allow only HMAC-SHA2-512/256 or UMAC-128
#   https://crypto.stackexchange.com/a/56432
```

#### Debugging `sshd` Issues

```shell
sudo sshd -t
# Test mode. Only check the validity of the configuration file and sanity of the keys.
```
```shell
sudo systemctl restart sshd
# On systemd based systems restart the sshd service
```

```shell
sudo systemctl status sshd
# On systemd based systems print the status of the sshd service
```
