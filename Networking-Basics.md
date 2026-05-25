# Networking Basics - TryHackMe Notes

# 1. What is a Network?

A network is simply: Devices connected together
Networks allow devices to communicate and share information.

# 2. Where Networks are Used

Networks exist everywhere in daily life.

## Examples

| Area             | Example                  |
| ---------------- | ------------------------ |
| Transportation   | Public transport systems |
| Electricity      | National power grid      |
| Communication    | Postal systems           |
| Smart Technology | Security cameras         |
| Internet         | Websites & servers       |


# 3. The Internet

The Internet is: A giant network made up of many smaller networks

## History of the Internet

| Year  | Event                         |
| ----- | ----------------------------- |
| 1960s | ARPANET project started       |
| 1989  | World Wide Web (WWW) invented |


## Important Person

* Tim Berners-Lee

# Types of Networks

## Private Network

Used inside homes, schools, or companies.

Example:

```text id="ol1wlh"
192.168.x.x
```

## Public Network

Used on the Internet.

Provided by:

* Internet Service Providers (ISP)


# 4. Device Identification in Networks

Devices need identities to communicate.

Devices use:

| Type        | Purpose           |
| ----------- | ----------------- |
| IP Address  | Logical identity  |
| MAC Address | Physical identity |

---

# 5. IP Addresses

IP stands for:

```text id="70o0ca"
Internet Protocol
```


## IPv4 Address Structure

Example:

```text id="9xhlta"
192.168.1.1
```

An IPv4 address contains:

* 4 sections
* Each section is called an **octet**


## IPv4 Example

| Octet 1 | Octet 2 | Octet 3 | Octet 4 |
| ------- | ------- | ------- | ------- |
| 192     | 168     | 1       | 1       |


## Public vs Private IP Example

| Device    | Private IP   | Public IP    |
| --------- | ------------ | ------------ |
| Desktop-1 | 192.168.1.77 | 86.157.52.21 |
| Desktop-2 | 192.168.1.74 | 86.157.52.21 |


# IPv4 Problem

IPv4 supports:

2^{32}

Possible addresses.

Approx:

```text id="6q1xaq"
4.29 Billion IP Addresses
```

Because of billions of devices, IPv4 addresses are running out.


# IPv6

IPv6 is the newer version of IP addressing.

Example IPv6:

```text id="g0s0e9"
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

---

## Advantages of IPv6

| Benefit            | Description                 |
| ------------------ | --------------------------- |
| Huge Address Space | Supports many more devices  |
| Better Efficiency  | Improved networking methods |
| Future Ready       | Solves IPv4 shortage        |

IPv6 supports:

2^{128}

Addresses.


# 6. MAC Addresses

MAC stands for:

```text id="oz8qis"
Media Access Control
```


## MAC Address Format

Example:

```text id="4r5v4t"
a4:c3:f0:85:ac:2d
```

## MAC Address Facts

* Physical address of a device
* Assigned by manufacturer
* Unique for each network interface
* Uses hexadecimal values


# MAC Address Structure

| Part               | Meaning          |
| ------------------ | ---------------- |
| First 6 Characters | Manufacturer     |
| Last 6 Characters  | Unique Device ID |



# 7. MAC Spoofing

MAC spoofing means:

```text id="y3kmrt"
Pretending to use another device's MAC address
```

Attackers may use spoofing to bypass security systems.


## Example

A firewall trusts the administrator’s MAC address.

If an attacker changes their MAC to the admin's MAC:

* Firewall may trust attacker traffic
* Security can fail


# 8. Ping & ICMP

## What is Ping?

Ping checks:

* Connectivity
* Response time
* Network reliability


## Protocol Used by Ping

```text id="d4zuw3"
ICMP
```

ICMP stands for:

```text id="c9s5xm"
Internet Control Message Protocol
```


# Ping Syntax

## Ping an IP Address

```bash id="aqt07u"
ping 10.10.10.10
```


## Example

```bash id="mryr4h"
ping 8.8.8.8
```


# Ping Results

Ping shows:

| Information      | Meaning               |
| ---------------- | --------------------- |
| Packets Sent     | Requests sent         |
| Packets Received | Replies received      |
| Time             | Delay in milliseconds |


# Important Flags

| Challenge        | Flag                        |
| ---------------- | --------------------------- |
| MAC Spoofing Lab | `THM{YOU_GOT_ON_TRYHACKME}` |
| Ping Challenge   | `THM{I_PINGED_THE_SERVER}`  |


# Important Networking Terms

| Term        | Meaning                   |
| ----------- | ------------------------- |
| Network     | Connected devices         |
| Internet    | Large network of networks |
| IP Address  | Logical device address    |
| MAC Address | Physical hardware address |
| IPv4        | Old IP version            |
| IPv6        | New IP version            |
| ICMP        | Protocol used by ping     |

---
