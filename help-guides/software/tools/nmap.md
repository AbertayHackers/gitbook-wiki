# Nmap

![FIXME](../../../.gitbook/assets/fixme.gif)

[https://nmap.org/](https://web.archive.org/web/20210125134507/https://nmap.org/)

## Introduction

Nmap is a security scanner used to discover hosts and services on a computer network, thus creating a “map” of the network. To accomplish its goal, Nmap sends specially crafted packets to the target host and then analyses the responses.

## More info

“The Stealth Syn scan \(-sS\) is considered to be the most reliable and quietest scan, and works by sending a SYN request to each TCP port. When a response is received it will commonly be one of two options: a SYN/ACK for an open port or an RST for a closed port. The scanner does not respond to the SYN/ACK packet, this never completing the connection and reducing the amount of network traffic used.

More information about running services can be gained through the use of the –sV scan, which attempts to perform banner detection among other additional tests on each port found to be open in an initial Stealth Syn scan. This more informative is also slower than a basic scan, and requires more traffic to complete”

