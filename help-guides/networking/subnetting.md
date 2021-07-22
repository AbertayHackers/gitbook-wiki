# Subnetting

*By [Isaac](../../members/isaac.md)*

Subnetting is the process of logically subdividing a network into one or more "subnets"

I will be using this [really good video on the subject](https://www.youtube.com/watch?v=ecCuyq-Wprc) as a guide, as learning this in a classroom environment can get quite tricky and pretty complicated.

The example the video gives is as follows:

```txt
One day your supervisor walks to you, saying: “here is the network ID 192.168.4.0/24,  please create three separate networks or subnets for a coffee shop: Sunny Cafe.”   The three separate subnets/networks are: One is for the office,  one for the front desk and storage room, and one is for public use. 

Your task is to list each subnet  network ID,  subnet mask,  Host ID Range, # of usable host IDs, and Broadcast ID.  One last question: How many subnets are wasted after subnetting? 
```

Our first step is to create a subnetting table, this table is always the same, and can be used as a cheat sheet for subnetting work you do in future:

|   Subnet    | 1    | 2    | **4**   | 8    | 16   | 32   | 664  | 128  | 256  |
| :---------: | ---- | ---- | ------- | ---- | ---- | ---- | ---- | ---- | ---- |
|    Host     | 256  | 124  | **64**  | 32   | 16   | 8    | 4    | 2    | 1    |
| Subnet Mask | /24  | /25  | **/26** | /27  | /28  | /29  | /30  | /31  | /32  |

- The first row is for the number of subnets you need
- The second row is the number of hosts, or IP addresses, in the subnet you're going to create
- The third row is for the subnet mask, a shorthand representing the number of "on" bits (1s) in a 32-bit binary integer, where 1s represent network bits, and 0s represent host bits. This is used to determine whether a host is on a local subnet or a remote network. Further information can be found [here](https://docs.microsoft.com/en-us/troubleshoot/windows-client/networking/tcpip-addressing-and-subnetting)

After this it's a simple case of determining how many subnets we need and then subsequently creating a table representing the IP addresses available to each subnet.

We have been tasked in the original example to create **three** subnets, however according to the reference table, we cannot create *just* three subnets, as a result of this we have to choose the lowest number of subnets that is still higher than three (in order to maximse space/efficiency). The number required for this is *four*, which is why the column with the number 4 at the top is bolded.

This is our table:

|  Network ID   | Subnet Mask |        Host ID Range        | No. of Usable Hosts | Broadcast ID  |
| :-----------: | :---------: | :-------------------------: | :-----------------: | :-----------: |
|  192.168.4.0  |     /26     |  192.168.4.1-192.168.4.62   |         62          | 192.168.4.63  |
| 192.168.4.64  |     /26     | 192.168.4.65-192.168.4.126  |         62          | 192.168.4.127 |
| 192.168.4.128 |     /26     | 192.168.4.129-192.168.4.190 |         62          | 192.168.4.191 |
| 192.168.4.192 |     /26     | 192.168.4.193-192.168.4.254 |         62          | 192.168.4.255 |

- The Network ID is the first IP address in the ID range, it designates the identity for the subnet that follows.
- The Subnet Mask always remains the same, and according to our table from earlier the mask to use in this instance is /26.
- The Host ID Range is the range of *usable* IP addresses in each subnet, these are the IDs that can be granted to devices on a subnet in order for it to gain internet access.
- Similar to the subnet mask, the number of usable hosts always remains the same due to the fact that each subnet is necessarily the same size. In this example there are 62 usable hosts because the first and last ID in any given subnet is reserved for the Network and Broadcast IDs respectively, and there are 64 total IDs because the maximum number of IDs on this network is 256, and 256 shared by 4 subnets is 64
- Finally, the Broadcast ID, or Broadcast Address, is the final address available in a subnet, it ensures that transmission to other nodes in a local network (and indeed beyond) is possible

