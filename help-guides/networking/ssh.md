

# Secure Shell (SSH)

By Mikey

- [OpenSSH Manual Pages](https://web.archive.org/web/20210125134545/https://www.openssh.com/manual.html)

## Guides

- [OpenSSH Guidelines](https://web.archive.org/web/20210125134545/https://infosec.mozilla.org/guidelines/openssh) (Mozilla)
- [Secure Secure Shell](https://web.archive.org/web/20210125134545/https://stribika.github.io/2015/01/04/secure-secure-shell.html) - [stribika](https://web.archive.org/web/20210125134545/https://twitter.com/stribika)
- [Securing SSH](https://web.archive.org/web/20210125134545/https://wiki.centos.org/HowTos/Network/SecuringSSH) (CentOS Wiki)

## Articles

- [The default OpenSSH key encryption is worse than plaintext](https://web.archive.org/web/20210125134545/https://latacora.singles/2018/08/03/the-default-openssh.html) (Latacora Blog)
- [ChaCha20 and Poly1305 in OpenSSH](https://web.archive.org/web/20210125134545/http://blog.djm.net.au/2013/11/chacha20-and-poly1305-in-openssh.html)
- [How Facebook does SSH at scale](https://web.archive.org/web/20210125134545/https://code.fb.com/security/scalable-and-secure-access-with-ssh/)

## Tools

- [ssh_scan](https://web.archive.org/web/20210125134545/https://github.com/mozilla/ssh_scan) “configuration and policy scanner” (Mozilla)

## Key Types

Key types are listed in the order of preference below:

1. `ED25519`
2. \>= 2048bit `RSA`

**Never** use `DSA` keys and avoid `ECDSA` keys if you can. Both [fail catastrophically on bad randomness](https://web.archive.org/web/20210125134545/https://security.stackexchange.com/questions/5096/rsa-vs-dsa-for-ssh-authentication-keys/46781#46781).

## Mobile

If you use SSH on the go often you'll want to look at using [Mosh](https://web.archive.org/web/20210125134545/https://mosh.org/)

### iOS

- [Termius](https://web.archive.org/web/20210125134545/https://www.termius.com/) [App Store](https://web.archive.org/web/20210125134545/https://itunes.apple.com/us/app/termius-ssh-shell-console-terminal/id549039908?mt=8) (free)
- [Prompt 2](https://web.archive.org/web/20210125134545/https://panic.com/prompt/) [App Store](https://web.archive.org/web/20210125134545/https://itunes.apple.com/gb/app/prompt-2/id917437289?mt=8) (£14.99)

## Examples

### Generate Keys

The `ssh-keygen` utility is used to create new SSH keys on most *nix systems.

#### ED25519

```
ssh-keygen -t ed25519 -a 100
```

- `-t`: Type of key to generate
- `-a`: Number of Key Derivation Function (KDF) rounds

#### RSA

```
ssh-keygen -t rsa -b 4096 -a 100
```

- `-t`: Type of key to generate
- `-b`: Size of key in bits
- `-a`: Number of (KDF) rounds

### Remove Hashed known_hosts Entry

If your client is set to hash known hosts e.g. has the following line in `~/.ssh/config`

```
HashKnownHosts yes
```

Then your `~/.ssh/known_hosts` file will be obfuscated.

To remove a host, when its hosts key changes, you'll need to execute:

```
ssh-keygen -R example.com
```

Which will remove all keys associated with that hostname from `~/.ssh/known_hosts`.

## Configuration

### Client

#### Permissions

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_*
chmod 644 ~/.ssh/id_*.pub
```

Only allow your user to access `~/.ssh` and your private keys, allow group and world to access your public keys.

#### config

Client configuration file, only lists no default settings.

- [config](https://web.archive.org/web/20210125134545/https://wiki.hacksoc.co.uk/_export/code/networking/ssh?codeblock=0)

  `# ~/.shh/config # ssh_config(5) Host * # For all hosts use the following directives     Protocol 2    # Use only protocol version two        IdentitiesOnly yes    # By default ssh will send all public keys (identities) in ~/.ssh to the server if you don't specify which key to use with -i    # This prevents that by only using the public keys explicitly configured in config or specified with -i          VisualHostKey yes    # Print an ASCII art representation of the remote host key fingerprint at login and for unknown host keys        HashKnownHosts yes    # Hash host names and addresses when they are added to ~/.ssh/known_hosts.    # ssh-keygen -R hostname    # Removes all keys belonging to hostname from a known_hosts file.     UseRoaming no    # Mitigates CVE-0216-0777        # Cryptography         KexAlgorithms curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521    # Define Key Exchange Algorithms    # NIST curves are listed for compatibility, curve25519 is preferred        HostKeyAlgorithms ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com    # Only allow ed25519 or RSA keys for client authentication        Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com    # Only use authenticated symmetric ciphers    # aes listed for compatibility, chacha20-poly1305 is preferred        MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com    # Only use encrypt then mac (etm) MACs    `

### Server

#### Permissions

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys 
```

Only allow your user to access `~/.ssh` and `~/.ssh/authorized_keys`. **These permissions are required** by the `StrictModes` directive.

#### sshd_config

Server configuration file, only lists none default settings.

- [sshd_config](https://web.archive.org/web/20210125134545/https://wiki.hacksoc.co.uk/_export/code/networking/ssh?codeblock=1)

  `# /etc/ssh/sshd_config # sshd_config(5) AddressFamily inet # Only use IPv4 ListenAddress x.x.x.x # Default is to listen on all local addresses # Better to specify an actual IP address to listen on Protocol 2 # Only use protocol version 2 LogLevel VERBOSE # Logs user's key fingerprint on login HostKey /etc/ssh/ssh_host_rsa_key HostKey /etc/ssh/ssh_host_ed25519_key # Key files cannot be group/world-accessible PermitRootLogin no # root user cannot login via SSH AuthenticationMethods publickey # Only allow public key authentication for login Subsystem sftp internal-sftp # Use sshd internal SFTP server code (plays nicer with Chroot)  # See https://serverfault.com/a/660325 for differences with  # Subsystem sftp /usr/libexec/openssh/sftp-server # If you just scp files you can disable this to reduce attack surface # Cryptography      KexAlgorithms curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521 # Define Key Exchange Algorithms # NIST curves are listed for compatibility, curve25519 is preferred     HostKeyAlgorithms ssh-ed25519,ssh-rsa # Only allow ed25519 or RSA keys for client authentication     Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com # Only use authenticated symmetric ciphers # aes listed for compatibility, chacha20-poly1305 is preferred     MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com # Only use encrypt then mac (etm) MACs    `