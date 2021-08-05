---
description: A beginner's introduction to homelabbing
---

# Home Lab

_Written by Sam \(_[_@Sam1ser_](https://twitter.com/Sam1ser)_\)_

This guide is a beginners introduction to homelabbing. It is by no means an all inclusive technical guide but more of a taster of what is possible with a homelab and why you might want to build your own.

## Why Build a Homelab?

Homelabs are a perfect environment for learning about computing, networking and security.

They provide a safe sandbox that you can use to run/deploy \(and subsequently learn about\) many applications and services. This is perfect for getting to know any applications/services that you may encounter during your studies or at work. For example, if you are looking into the security of LDAP and Active Directory, you can just set up your own Active Directory server and experiment with it yourself.

They can be very easy to configure or very hard to configure, it's entirely up to you how much of a challenge you want to face. If you just want to self-host pre-packaged services, it's fairly easy. If you want to create your own systems and configure them from scratch - or even write your own services - this will be more challenging. Again, it's up to you.

They also involve a fair bit of networking. You may be configuring connections between several devices and will be implementing access from your preexisting LAN, or maybe even constructing a completely new LAN, as well as potentially allowing external access.

Tinkering and constructing your very own labbing environment from the ground up is a very fun and rewarding process. Going from having an idea to actually building and implementing it yourself is something that never gets old. You will also find that the more things you create the more you will learn, and the more you learn the grander your ideas will become.

If this all sounds intimidating and confusing then you are a perfect candidate for creating a homelab. It's much better to face an intimidating environment in the comfort of your own home than to face one for the first time in the real world.

It's an endless cycle of learning, developing, and creating. You will learn an immense amount just from setting up the lab let alone all of the things you can explore once you have a labbing environment.

### Practical Homelab Ideas

If you want to embark on this journey but don't have any specific projects in mind, here are a few ideas to start you off with.

#### Virtual Network for Pentesting and Research

From a hacker's perspective, homelabs are perfect for testing and developing all kinds of skills.

For red teamers you can find many vulnerable virtual machines and web applications on the internet that you can download and host yourself on your own hardware. This provides a safe, isolated environment for honing your pentesting skills.

For blue teamers you can set up networking monitoring services like splunk and experiment that way.

You could also just set up particular services that you want to test the security of. A particularly good way to do this is to install older versions of common services and try and exploit them.

Another use is to learn about services from the sysadmin's perspective. If you know how a system is typically configured and how it works, it will be easier to try and find potential misconfigurations and exploit them in the future.

#### Home Media Server

You could go for an all in one package \(plex/emby\) and have all of your movies and music organised there. Or maybe you might want to use something like Calibre to host ebooks. Then you might set up external access and be able to access your media from anywhere.

#### Web Server

If you want to run a blog, why not host it yourself? Homelabs usually make for ideal webservers. You do however need to be security conscious when exposing any part of your network to the internet.

#### Game Server

Many games will allow you to host your own private server. Minecraft is great, but it's even greater if you've got your own server for you and your friends. Once again, this comes with security risks. Particularly if you decide to host a public server.

#### Set Up A Pihole

A Pihole replaces your network's DNS server and blocks all adverts on all connected devices.

[Here is a guide](pihole.md) with more information and how to configure your own.

## Homelab Components

There is no one optimal homelab configuration. Every homelab will have different purposes and thus will be configured differently. It is possible, however, to generalise what a homelab is made of. This may be helpful when first designing your own set up. This section will give an overview of the components of a homelab.

It should also be kept in mind that while the components here will be described as physical, many of them can be virtualised. It is your decision how much of your lab should be physical and how much should be virtual.

A homelab setup can be broken down into three general components:

**Computer hardware** is used to run your virtual machines and containers.

**Network hardware** is used to route traffic between your Computer Hardware, your VMs/Containers, and the Internet.

The **Hypervisor** is the software used to create, manage and control your VMs and Containers.

The following sections will cover all three in detail. If you already have Computer hardware, skip to Network hardware. If you already have Network hardware too, skip to Hypervisors.

### Computer Hardware

With hardware - from a student's perspective - you're looking to balance power, maintenance cost and noise levels. Before you start hitting up ebay to try and grab some enterprise grade rack mounted gear you should first consider two things:

* What hardware do you already own?
* What is the scale of your project?

You \(most likely\) do not need to buy anything to start homelabbing right now!

The first thing you should be doing when considering a homelab build is what you already have access to. Do you have an old desktop lying around? Start with that. Or maybe a disused laptop. That will work too! You do not need a very powerful computer to power your homelab.

Even if you only have your daily driver PC or laptop, everything you could want to do with a homelab can be virtualised. Coding, Linux, Containers, VMs, Networking and more can all be done with just your PC that you are already using. However, if you are reading this guide, that's probably not sufficient.

If you have looked into homelabs before \(/r/homelab\) you may be imagining a massive rack filled with servers, switches and routers but really you don't want this while first starting out. It's feasible to buy some rack mounted gear at the beginning but it will be better to start with whatever you can get you hands on.

As you create your homelab you may run into some hardware restrictions. For example: not having enough RAM to host all the VMs you want to host, or your CPU might just not be powerful enough to cut it. This is when you should start looking into getting better hardware.

Of course if your initial purpose of building a homelab requires power that you don't already have access to, you should get hardware that is sufficient for your needs.

The key thing to remember is this: **building a homelab doesn't have to be expensive.** It absolutely can be, but it doesn't have to be.

#### Hardware Pros and Cons

Something to consider with hefty server hardware is it can be loud and expensive to run due to the cost of electricity.

Before buying some new kit, it's worth finding out how much it will cost to run by finding the wattage, converting it to kilowatt-hours \(kWh\) and then multiplying that by how much your electricity provider charges you per kWh.

A lot of hardware uses really noisy fans, so if you are in a confined living situation and can't sort out sufficient noise blocking take this into consideration! There is also a lot of hardware that operates near silently. Look for fanless systems.

You probably won't want to run your main production machine 24/7, which is often useful when running services like websites and game servers. Having a seperate server allows for 24/7 uptime on your services.

Using seperate machines to host front-facing services is also far more secure than hosting them on your main PC. It is a really bad idea to open up ports on your main PC to the internet for obvious reasons…

One of the main reasons for homelabbing is to learn about different hardware and it's really fun and satisfying to set up your own physical network. If you have the space and the budget, it's worth it.

#### Components

When thinking about server hardware you will need to think about specs differently from how you might when building a PC.

The quantity of RAM is far more important for a homelab server than for a PC. Each virtual machine will need to have some RAM dedicated to it. If you are running lots of virtual machines, the amount of memory you are using can add up very quickly.

The other most important component to consider is your storage space. Again, hosting lots of virtual machines all with virtual hard drives can quickly add up to requiring a lot of storage. You also will be better of with faster read/write speeds. When buying hard drives, you should also consider redundancy, how you plan to protect your data and your preferred RAID configuration. I would recommend either getting two drives and using RAID 1 or getting four drives and using RAID 1+0.

A powerful CPU will be useful for running more intensive services and for running more concurrent VMs. A recent generation intel i3 processor will, in most cases, be completely sufficient. You should make sure that your processor supports Hardware Virtualisation. For Intel this is known as “Intel VT” and for AMD it's “AMD-V”. It's not vital, but it is required to run 64 bit VMs.

You probably won't need a graphics card in your server. It would be useful for running tasks like password cracking or rendering things, but at least while starting out it will be easier to go without a dedicated GPU. If you want to run programs that would be more efficient on a GPU you should just look into renting the GPU power from a service like AWS.

**Importantly** this hardware information may be completely wrong for the lab you need. Again, this guide is aimed at people who want a fairly flexible set up.

#### Single Host Virtualisation

The most basic homelab setup is to have a single host \(a computer\) running all of your virtual machines/containers.

The host will be running a hypervisor. This is required to distribute the host's resources between virtual machines. It can be either bare metal, running directly on the host's hardware, or embedded, running as software on a host operating system.

If you have used vmware or virtualbox you have already used an embedded hypervisor.

Typically with a homelab you should be using a bare metal hypervisor as this will get the best performace for your virtual machines out of your hardware.

This setup is a good choice when starting out.

#### Physical Cluster

This is having multiple physical machines to run your virtual machines/containers. This setup is closer to an enterprise setup and will provide you with the most flexibility when it comes to testing and learning things on your network.

This setup is also the most easily scalable as to add more power to your lab you can just add more hosts, rather than upgrading the parts of an individual host.

This can potentially be paired with a NAS \(Network Attached Storage\) device for more a more flexible and reliable storage solution. This is a seperate host where you would install your hard drives, then the main host running the hypervisor will mount these drives over the network.

This setup is a good one to move to once you're finding your single host setup to be lacking. It's also really fun.

### Network Hardware

If the computer hardware is the brain, the network hardware is the nervous system. It will allow your devices to communicate with each other, allowing you to access the services you're hosting and allowing you to remotely connect and configure your host/hosts.

Networking tends to be quite an intimidating aspect of homelabbing. This section will explain a basic network configuration which can be expanded on fairly easily.

In this section it is assumed you have a very basic understanding of networking. This includes subnets, netmasks, firewalls, LAN/WAN and the OSI model. You will not need to know the ins and outs of these things, just have a basic idea of what they are. If at any point in the guide you read something and don't understand it, you should be able to just google it and find out enough. If you're really stuck, ask in the slack.

#### Switch

The switch is, at its most basic, what controls the packet flow of the network. Operating at layer 2 of the OSI model, it uses MAC addresses to forward packets between hosts. To connect to a switch you will need an ethernet port, aka a NIC. If your laptop/main device doesn't have a NIC you can get usb NIC fairly cheaply.

Going deeper, there are two kinds of switches to consider: managed and unmanaged. Unmanaged switches are pretty much plug-n-play. You will be able to connect your hosts and allow them to communicate, but not much more.

Managed switches however give you more control over your LAN traffic. You can do everything you can do with an unmanaged switch, and much more.

Some features I find very useful are VLANs, QoS and Link Aggregation.

VLANs \(Virtual LANs\) allow you to segregate your network into seperate isolated groups. This can be useful in many homelab situations, but an example is having a guest wireless network and a private wireless network. The guest network allows your guests to connect to the internet using your Wi-Fi but without giving them access to your homelab hosts. Very useful!

QoS \(Quality of Service\) allows you to prioritise certain network traffic. For example, streaming movies from your media server could be prioritised over webserver access. Again, you can probably imagine many more uses for this.

Finally, Link Aggregation, which allows you to use two NICs connected to two ports on the switch and combine their bandwidth for one data stream. This not only increases the bandwidth significantly but also increases the reliability of the connection. Particularly useful for a NAS, which will probably be one of the more bandwidth intensive hosts on your network.

So, as you can probably tell by now, a managed switch is probably best for a homelab.

Another thing to consider is PoE \(Power over Ethernet\) ports. These are useful for powering smaller devices on your network like Wi-Fi access points. All you need to do is connect the ethernet cable and the device will run off the power supplied by the switch through the cable. Raspberry Pis also have a PoE hat, which can make for nice discreet IoT type devices.

**However** PoE ports usually require cooling systems. These can be very noisy, so be careful! If you are in a confined space without good noise insulation, you will regret buying a fully PoE switch. You should ideally be looking for a fanless switch.

For your homelab, you - initially - will not need many ports. An eight port switch will do you fine. The price of switches doesn't really scale with the number of ports though, so basically just go with what you find. Again, if you need advice about a certain switch that you're thinking of buying, google and slack are your friends.

So, in summary, you will probably want to aim for a fanless, managed switch. Ebay is a good place to get hunting.

#### Router

Your router is primarily used as the interface between your LAN and the internet \(WAN\). It functions on layer 3 of the OSI model and uses IP addresses for packet forwarding.

The router you are currently using is probably whatever was supplied by your ISP. For example, the Virgin Media Super Hub 3. This is a basic router with basic functionality.

#### Ethernet Cable

Though you have almost definitely used ethernet cable before, it will be useful to know about different types of ethernet cable, and how to make your own, before investing in some for your lab.

For the standard Homelab the LAN Connection will be established with a RJ-45 headed Ethernet cable. This would likely connect into a [Switch](./#switch) or [Router](./#router) as discussed above. 

![RJ-45 headed Ethernet cable](../../.gitbook/assets/image%20%282%29%20%282%29%20%282%29%20%282%29%20%281%29.png)

It is recommended that the minimum Category for Ethernet cables for Homelabs would be Cat5e; as it is able to reach speeds of up to 1 Gbps. The Category of your Ethernet cable is very simple yet important as it could be the bottleneck of your interconnectivity. Bandwidths of &gt;1Gbps is **strongly** recommended for NAS setups along with RAID to ensure said bandwidth can be properly saturated.
