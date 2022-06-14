# LINUX Week 02
## Remote Operation

Open the option in Remote Display (Enable Server), replace the default Server Port, and then open Allow Multiple Connections, you can perform remote desktop operations

At the beginning of the opening match, you can connect to the remote desktop (graphical operation) and use the local connection (127.0.0.1:your port)
## Network

The default network type is NAT mode, but I will explain to you the other

* Not Attached

A virtual network adapter is installed in a VM, but the network connection is missing, much like when you unplug the Ethernet network cable when using a physical network adapter. This mode can be useful for testing. For example, you can enable this network mode for a short time to emulate unplugging the cable. When you disable the Not Attached mode by switching to another network node, the network connection becomes available again. You can also check whether a DHCP client obtains the IP address correctly, whether the appropriate application can resume downloading after link interruption or packet loss, and so on.

* NAT

This network model is enabled for a virtual network adapter by default. A guest operating system on a VM can access hosts in a physical local area network (LAN) by using a virtual NAT (Network Address Translation) device. External networks, including the internet, are accessible from a guest OS. A guest machine is not accessible from a host machine, or other machines in the network when the NAT mode is used for VirtualBox networking. This default network mode is sufficient for users who wish to use a VM just for internet access.

* NAT Network

This mode is similar to the NAT mode that you use for configuring a router. If you use the NAT Network mode for multiple virtual machines, they can communicate with each other via the network. The VMs can access other hosts in the physical network and can access external networks including the internet. Any machine from external networks as well as those from a physical network to which the host machine is connected cannot access the VMs configured to use the NAT Network mode (similarly to when you configure a router for internet access from your home network). You cannot access the guest machine from the host machine when using the NAT Network mode (unless you are configuring port forwarding in global VirtualBox network settings). A built-in VirtualBox NAT router uses a physical network interface controller of the VirtualBox host as an external network interface (as is the case for the NAT mode).

* Bridged Adapter

This mode is used for connecting the virtual network adapter of a VM to a physical network to which a physical network adapter of the VirtualBox host machine is connected. A VM virtual network adapter uses the host network interface for a network connection. Put simply, network packets are sent and received directly from/to the virtual network adapter without additional routing. A special net filter driver is used by VirtualBox for a bridged network mode to filter data from the physical network adapter of the host.

* Internal Network

Virtual machines whose adapters are configured to work in the VirtualBox Internal Network mode are connected to an isolated virtual network. VMs connected to this network can communicate with each other, but they cannot communicate with a VirtualBox host machine, or with any other hosts in a physical network or external networks. VMs connected to the internal network cannot be accessed from a host or any other devices. The VirtualBox internal network can be used for modeling real networks.

* Host-only Adapter

This network mode is used for communicating between a host and guests. A VM can communicate with other VMs connected to the host-only network, and with the host machine. The VirtualBox host machine can access all VMs connected to the host-only network.

* Generic Driver

This network mode allows you to share the generic network interface. A user can select the appropriate driver to be distributed in an extension pack or be included with VirtualBox.

## Some Command That You Can Use

* Shutdown : `halt -p ` 、  `poweroff` 、`shutdown` 
* Change To Super User: `su`
>note : password in linux will be blank and not show anything
* Change Directory : `cd`
* `gedit a.txt` : can edit the content of the file, use a graphical interface, and create a file if there is no file
* `cat a.txt` 、`more a.txt` 、`less a.txt` to see the file content
* To Show Network Information : `ifconfig`

## Snapshot

Snapshots allow you to save a particular state of a VM; this can be handy when you want to test something, or you’re about to make a change to that VM, and you need to be able to roll back to a working instance. Not only does this save you a lot of headaches, but it can be a serious time-saver.