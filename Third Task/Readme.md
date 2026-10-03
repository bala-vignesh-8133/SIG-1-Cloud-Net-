# Cisco Packet Tracer: Ping Failure Diagnosis and OSI Layer Troubleshooting

## Project Overview

This project demonstrates systematic network troubleshooting using Cisco Packet Tracer. It focuses on identifying and resolving common connectivity failures through IPv4 configuration checks, ICMP ping tests, ARP inspection, physical link verification, and Simulation Mode packet analysis.

The lab uses two workstations connected through a Layer 2 switch to demonstrate how network configuration errors and physical connectivity problems affect communication.

## Objectives

* Diagnose common network connectivity failures.
* Verify IPv4 addressing and subnet configuration.
* Identify physical link and data-link connectivity problems.
* Understand ARP address resolution and ICMP communication.
* Analyze packet flow using Cisco Packet Tracer Simulation Mode.
* Apply corrective actions and verify connectivity restoration.

## Network Topology

The network consists of two PCs connected to a central Layer 2 switch.

* PC0
* PC1
* Switch0

### IP Addressing Table

| Parameter       | PC0           | PC1           |
| --------------- | ------------- | ------------- |
| IPv4 Address    | 192.168.10.25 | 192.168.10.26 |
| Subnet Mask     | 255.255.255.0 | 255.255.255.0 |
| Default Gateway | Not required  | Not required  |

Both PCs belong to the same IPv4 subnet, so a router is not required for communication between them.

## Tools and Technologies

* Cisco Packet Tracer
* IPv4 addressing
* ICMP
* ARP
* Ethernet switching
* OSI reference model
* Network troubleshooting utilities

## Troubleshooting Scenarios

### 1. Incorrect IP Address or Subnet

Compare the IPv4 configuration of both PCs using `ipconfig /all`. Verify that the addresses and subnet masks are consistent with the intended network.

### 2. Default Gateway Configuration

Inspect the default gateway when troubleshooting communication with remote networks. A gateway is not required for communication between hosts on the same subnet.

### 3. Duplicate IP Address

Assigning the same IPv4 address to two devices can cause address conflicts and inconsistent connectivity. Restore unique IP addresses and verify communication.

### 4. Physical Link Failure

Inspect Ethernet cables, switch ports, and link indicators. Restore the physical connection before repeating connectivity tests.

### 5. ARP Resolution

Inspect ARP requests and replies to understand how a host discovers the destination MAC address before transmitting an Ethernet frame to another local host.

### 6. ICMP Packet Analysis

Use Simulation Mode to observe ICMP echo requests and replies and investigate where packets are delayed or dropped.

## Diagnostic Commands

### Verify Local TCP/IP Functionality

```text
ping 127.0.0.1
```

### Verify the Local IPv4 Address

```text
ipconfig
```

### Display Detailed IP Configuration

```text
ipconfig /all
```

### Ping the Local Host Address

```text
ping 192.168.10.25
```

### Test Communication Between PCs

```text
ping 192.168.10.26
```

### Inspect the ARP Cache

```text
arp -a
```

## Troubleshooting Methodology

The lab follows a bottom-up troubleshooting approach:

1. Verify the physical connection and Ethernet link status.
2. Inspect local interface configuration.
3. Compare IPv4 addresses and subnet masks.
4. Check for duplicate addresses and ARP resolution problems.
5. Test connectivity using ICMP ping.
6. Inspect ARP and ICMP events in Simulation Mode.
7. Apply corrective actions and repeat the tests.
8. Document the final configuration and results.

## OSI Layer Mapping

| Layer               | Troubleshooting Focus                      |
| ------------------- | ------------------------------------------ |
| Layer 1 – Physical  | Ethernet cabling and link status           |
| Layer 2 – Data Link | Switching, Ethernet frames, and ARP        |
| Layer 3 – Network   | IPv4 addressing, subnet masks, and routing |

## Expected Results

After correcting the simulated faults:

* Both PCs have unique IPv4 addresses.
* Both PCs use the intended subnet mask.
* Ethernet links are operational.
* ARP resolves the destination MAC address.
* ICMP echo requests and replies are observed.
* PC0 and PC1 can communicate successfully.

## Screenshots

The `Screenshots` directory contains evidence of the network topology, IP configuration, connectivity tests, troubleshooting scenarios, and packet analysis.

## Project Files

The `PacketTracer` directory contains the Cisco Packet Tracer project file.

Open the `.pkt` file in Cisco Packet Tracer to inspect the topology and repeat the troubleshooting exercises.

## Conclusion

This lab demonstrates a structured approach to diagnosing network connectivity failures in Cisco Packet Tracer. By combining configuration verification, ICMP testing, ARP inspection, physical link checks, and Simulation Mode analysis, it develops practical skills in identifying network faults and verifying corrective actions.
