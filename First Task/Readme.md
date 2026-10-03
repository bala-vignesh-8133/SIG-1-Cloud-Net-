# Single-Host Static IPv4 Addressing & Local Loopback Verification

## Lab Overview

This lab demonstrates how to configure a standalone workstation with a static IPv4 address in Cisco Packet Tracer and verify the network configuration using Command Prompt utilities.

The lab also verifies the local TCP/IP protocol stack and the assigned network interface using `ping`.

## Objectives

* Configure a static IPv4 address on PC0.
* Configure the subnet mask, default gateway, and DNS server.
* Verify the IP configuration using `ipconfig /all`.
* Test the local TCP/IP protocol stack using the loopback address.
* Verify the assigned IPv4 address using `ping`.

## Tools Used

* Cisco Packet Tracer
* Command Prompt
* IPv4 Networking

## Network Configuration

| Parameter       | Configuration   |
| --------------- | --------------- |
| Device          | PC0             |
| Interface       | FastEthernet0   |
| IPv4 Address    | `192.168.10.25` |
| Subnet Mask     | `255.255.255.0` |
| CIDR            | `/24`           |
| Default Gateway | `192.168.10.1`  |
| DNS Server      | `8.8.8.8`       |

## Configuration Steps

### 1. Add PC0

A generic PC was added from the End Devices section in Cisco Packet Tracer.

### 2. Configure Static IPv4

Navigate to:

**PC0 → Desktop → IP Configuration → Static**

Enter the following values:

```text
IPv4 Address:    192.168.10.25
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.10.1
DNS Server:      8.8.8.8
```

### 3. Verify IP Configuration

Open:

**PC0 → Desktop → Command Prompt**

Run:

```bash
ipconfig /all
```

The output should confirm that FastEthernet0 is configured with:

```text
IPv4 Address: 192.168.10.25
Subnet Mask: 255.255.255.0
```

### 4. Test the Local TCP/IP Stack

Run:

```bash
ping 127.0.0.1
```

The loopback address `127.0.0.1` is used to verify the local TCP/IP protocol stack.

### 5. Verify the Assigned IP Address

Run:

```bash
ping 192.168.10.25
```

A successful response confirms that the configured interface responds to its assigned IPv4 address.

## Verification Results

| Test                    | Expected Result               | Status |
| ----------------------- | ----------------------------- | ------ |
| Static IP Configuration | Correct IPv4 parameters       | Passed |
| `ipconfig /all`         | 192.168.10.25 / 255.255.255.0 | Passed |
| `ping 127.0.0.1`        | Reply received, 0% loss       | Passed |
| `ping 192.168.10.25`    | Reply received, 0% loss       | Passed |

## Screenshots

### 1. Packet Tracer Topology

![Packet Tracer Topology](screenshots/01-topology.png)

### 2. Static IP Configuration

![IP Configuration](screenshots/02-ip-configuration.png)

### 3. IP Configuration Verification

![ipconfig /all](screenshots/03-ipconfig-all.png)

### 4. Ping Verification

![Ping Verification](screenshots/04-ping-verification.png)

## Project Files

* `Single-Host-IPv4-Verification.pkt` — Cisco Packet Tracer project
* `README.md` — Lab documentation
* `screenshots/` — Configuration and verification screenshots

## Key Learning

This lab provided practical experience with:

* Static IPv4 addressing
* Subnet masks and `/24` networks
* Default gateway configuration
* DNS configuration
* `ipconfig /all`
* IPv4 loopback testing
* `ping` for connectivity verification
* Basic network troubleshooting using Cisco Packet Tracer

## Conclusion

The standalone workstation PC0 was configured with the required static IPv4 parameters. The configuration was verified using `ipconfig /all`, while loopback and host-address ping tests were used to verify the local TCP/IP stack and network interface configuration.
