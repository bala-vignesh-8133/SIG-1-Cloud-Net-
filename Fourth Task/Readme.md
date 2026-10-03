# Day 4: Subnet Mismatch and ARP Resolution Failure

## Overview

This lab demonstrates IPv4 subnet mismatch troubleshooting, Address Resolution Protocol (ARP), and ICMP connectivity testing using Cisco Packet Tracer.

Two PCs are connected to a Cisco Catalyst 2960 switch. Initially, the hosts are configured with IPv4 addresses belonging to different subnets. Connectivity tests are performed to examine how subnet masks affect local and remote destination identification.

The lab also demonstrates ARP resolution failure by attempting to communicate with an unused IPv4 address. Finally, the IP addressing configuration is corrected and connectivity is verified.

## Objectives

* Understand IPv4 subnetting and subnet masks.
* Identify connectivity problems caused by incorrect IP addressing.
* Observe ARP requests using Simulation Mode.
* Understand the relationship between ARP resolution and ICMP ping.
* Analyze packet events using the Packet Tracer PDU Information window.
* Correct subnet configuration errors.
* Verify connectivity using Command Prompt utilities.

## Network Topology

Devices used:

* PC0
* PC1
* Cisco Catalyst 2960 switch
* Two Copper Straight-Through Ethernet cables

Both PCs connect directly to the switch.

## Initial IP Addressing

| Parameter       | PC0            | PC1            |
| --------------- | -------------- | -------------- |
| IPv4 Address    | 192.168.10.10  | 192.168.20.20  |
| Subnet Mask     | 255.255.255.0  | 255.255.255.0  |
| Prefix Length   | /24            | /24            |
| Default Gateway | Not configured | Not configured |

The two hosts belong to different IPv4 subnets.

When PC0 attempts to reach PC1, it considers the destination to be on a remote network. Since no default gateway is configured, PC0 cannot forward traffic to the destination.

## Simulation Procedure

1. Create the topology using PC0, PC1, and a Cisco 2960 switch.
2. Connect both PCs to the switch using Copper Straight-Through cables.
3. Configure the initial IP addresses.
4. Switch to Simulation Mode.
5. Configure the event filters to display ARP and ICMP.
6. Attempt to ping PC1 from PC0.
7. Observe the connectivity failure.
8. Change PC0's subnet mask to `255.255.0.0`.
9. Ping the unused address `192.168.30.30`.
10. Observe the ARP request and the absence of an ARP reply.
11. Restore PC0's subnet mask to `255.255.255.0`.
12. Configure PC1 with IPv4 address `192.168.10.11`.
13. Verify connectivity using the ping command.

## ARP Resolution Failure

With PC0 configured as `192.168.10.10/16`, the destination address `192.168.30.30` is considered local.

PC0 broadcasts an ARP request to discover the destination MAC address. Because no device owns the requested IPv4 address, no ARP reply is returned.

PC0 cannot resolve the destination MAC address and therefore cannot transmit the corresponding ICMP Echo Request to that destination.

This demonstrates how unsuccessful ARP resolution can prevent IPv4 communication over Ethernet.

## Corrected IP Configuration

| Parameter       | PC0           | PC1           |
| --------------- | ------------- | ------------- |
| IPv4 Address    | 192.168.10.10 | 192.168.10.11 |
| Subnet Mask     | 255.255.255.0 | 255.255.255.0 |
| Prefix Length   | /24           | /24           |
| Default Gateway | Not required  | Not required  |

Both hosts now belong to the `192.168.10.0/24` subnet.

## Verification Commands

### Test Connectivity

```text
ping 192.168.10.11
```

Expected result: Successful ICMP Echo Replies from PC1.

### Inspect the ARP Cache

```text
arp -a
```

Expected result: An ARP table entry for PC1's IPv4 address after successful address resolution, if supported by the simulated PC.

### Inspect IP Configuration

```text
ipconfig
```

Expected result: The configured IPv4 address and subnet mask are displayed.

### Test the Local TCP/IP Stack

```text
ping 127.0.0.1
```

Expected result: Successful loopback replies, indicating that the local TCP/IP stack responds to the test.

## OSI Layer Analysis

| Layer   | Component                       | Purpose                                                                 |
| ------- | ------------------------------- | ----------------------------------------------------------------------- |
| Layer 1 | Ethernet cabling and interfaces | Provides physical connectivity.                                         |
| Layer 2 | Ethernet and ARP                | Forwards frames and resolves IPv4 addresses to MAC addresses.           |
| Layer 3 | IPv4 and ICMP                   | Handles IP addressing, destination selection, and connectivity testing. |

## Troubleshooting Findings

* A working physical connection does not guarantee IP connectivity.
* Subnet masks determine whether a destination is considered local or remote.
* ARP resolves local IPv4 addresses to MAC addresses.
* An unanswered ARP request prevents a host from resolving the destination MAC address.
* A subnet mask mismatch does not automatically prevent a host from answering an ARP request for its own IPv4 address.
* A successful ping requires appropriate forward and return communication paths.
* Configuring both hosts in the same subnet allows direct communication without a router in this topology.

## Screenshots

Store the screenshots in the `screenshots/` directory.

Recommended evidence:

1. Network topology.
2. Initial PC0 configuration.
3. Initial PC1 configuration.
4. Failed ping with the initial subnet mismatch.
5. ARP simulation.
6. ARP resolution failure for the unused destination.
7. Corrected IP configuration.
8. Successful ping after correction.

## Files

* `Day-04-Subnet-Mismatch.pkt` — Cisco Packet Tracer project.
* `README.md` — Lab documentation.
* `screenshots/` — Configuration and verification evidence.

## Conclusion

This lab demonstrates the importance of correct IPv4 addressing and subnet masks in a switched network. Simulation Mode provides visibility into ARP and ICMP events, helping identify where communication fails.

By analyzing packet behavior and correcting the addressing configuration, connectivity between the two hosts can be established and verified.
