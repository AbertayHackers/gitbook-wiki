# Wireshark

![FIXME](../../.gitbook/assets/fixme.gif)

[Wireshark](https://web.archive.org/web/20210125134512/https://wireshark.org/) is a network traffic monitoring tool.

### basic usage

This is covered really well [here](https://web.archive.org/web/20210125134512/https://jvns.ca/blog/2018/06/19/what-i-use-wireshark-for/)

### slightly advanced tricks

- [add any field as a custom column](https://web.archive.org/web/20210125134512/https://www.malware-traffic-analysis.net/tutorials/wireshark/index2.html) (or you can do it from prefs)
- [add geoip db](https://web.archive.org/web/20210125134512/https://wiki.wireshark.org/HowToUseGeoIP) and then go to Statistics > Endpoints and you can see the IPs plotted out on a map
- [decrypt tls](https://web.archive.org/web/20210125134512/http://packetpushers.net/using-wireshark-to-decode-ssltls-packets/) by importing the cert
- [decrypt WPA encrypted wifi](https://web.archive.org/web/20210125134512/https://wiki.wireshark.org/HowToDecrypt802.11)

### SSHdump

You can capture packets from an interface on a remote machine using SSH and tcpdump.

On Mac/Ubuntu this is built into Wireshark by default and you can select it as an option from the capture interface screen. (I think on Windows there's a plugin. Go find out and update this wiki!)

You just give it the SSH details and it runs tcpdump on the remote machine.