# Domain Name System (DNS)

![FIXME](../../.gitbook/assets/fixme.gif)

## Override DHCP Nameservers (Debian/ Ubuntu)

[Source](https://web.archive.org/web/20210125134502/http://unix.stackexchange.com/a/154538)

```bash
sudo nano /etc/dhcp/dhclient.conf
```

Add the following line replacing `8.8.8.8` with the IP of your server.

```
supersede domain-name-servers 8.8.8.8;
```

Restart Networking so the change takes affect.

```bash
sudo service networking restart 
```

You can test the change by running something like `dig google.com` then check that `SERVER:` matches the value you added to `dhclient.conf` above.