# Peer-to-Peer LAN Verification

## Overview

This project demonstrates the configuration and verification of a basic Peer-to-Peer Local Area Network using **Cisco Packet Tracer**. Two workstations are connected through a **Cisco 2960 Layer 2 switch** and configured with static IPv4 addresses within the same subnet.

## Network Topology

```text
PC0 ───────── Switch0 ───────── PC1
     Fa0/1             Fa0/2
```

## IP Addressing

| Device  | Interface     | IPv4 Address  | Subnet Mask   | Default Gateway |
| ------- | ------------- | ------------- | ------------- | --------------- |
| PC0     | FastEthernet0 | 192.168.10.25 | 255.255.255.0 | 192.168.10.1    |
| PC1     | FastEthernet0 | 192.168.10.26 | 255.255.255.0 | 192.168.10.1    |
| Switch0 | —             | Default       | —             | —               |

## Configuration

* Added two end devices (PC0 and PC1).
* Added a Cisco 2960 Layer 2 switch.
* Connected both PCs using Copper Straight-Through cables.
* Configured static IPv4 addressing on both workstations.
* Verified the physical links and network interfaces.

## Verification

### 1. IP Configuration

The `ipconfig` command was used to verify the IPv4 configuration of PC0.

```text
ipconfig
```

### 2. Connectivity Test

ICMP connectivity between PC0 and PC1 was verified using:

```text
ping 192.168.10.26
```

Successful replies confirmed end-to-end communication within the local subnet.

### 3. ARP Verification

The ARP cache was inspected using:

```text
arp -a
```

The presence of an entry for `192.168.10.26` confirmed successful IP-to-MAC address resolution.

## Verification Summary

| Test       | Purpose                      | Result     |
| ---------- | ---------------------------- | ---------- |
| `ipconfig` | Verify IP configuration      | Successful |
| `ping`     | Verify PC-to-PC connectivity | Successful |
| `arp -a`   | Verify IP-to-MAC resolution  | Successful |

## Tools Used

* Cisco Packet Tracer
* IPv4
* ICMP
* ARP
* Layer 2 Switching

## Conclusion

The Peer-to-Peer LAN was successfully implemented and verified. Static IPv4 configuration, physical connectivity, ICMP communication, and ARP resolution were confirmed between PC0 and PC1 through the Layer 2 switch.
