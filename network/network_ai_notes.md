# Architecture Diagrams and Formal Definitions

## Network Architecture

### Formal Definition

A computer network is a collection of interconnected devices that communicate and share resources using standardized communication protocols.

### Architecture Diagram

```text
                    INTERNET
                        |
                        |
                    [Router]
                        |
                ----------------
                |              |
            [Switch]       [WiFi AP]
                |              |
        ----------------    --------
        |      |      |      |     |
      PC1    PC2   Server  Mobile Laptop
```

### Explanation

* Router connects the local network to the internet.
* Switch connects wired devices.
* WiFi Access Point connects wireless devices.
* End devices communicate through these networking devices.

### Layman Explanation

Think of a school:

* Principal Office = Router
* Hallways = Switch
* Classrooms = Devices
* Students = Data

Students move through hallways to reach different classrooms.

---

# NIC Architecture

### Formal Definition

A Network Interface Card (NIC) is a hardware component that enables a device to connect and communicate over a computer network.

### Diagram

```text
+----------------------+
|      COMPUTER        |
|                      |
|  +---------------+   |
|  |     NIC       |   |
|  +---------------+   |
+----------|-----------+
           |
           |
     Ethernet Cable
           |
           |
      Network Switch
```

### Layman Explanation

NIC is like the mouth and ears of a computer for network communication.

Without it, the computer cannot speak or listen to other computers.

---

# MAC Address Architecture

### Formal Definition

A Media Access Control (MAC) Address is a unique hardware identifier assigned to a NIC by the manufacturer.

### Example

```text
00:1A:2B:3C:4D:5E
```

### Diagram

```text
Computer
   |
   |
[NIC]
   |
   |
MAC Address
00:1A:2B:3C:4D:5E
```

### Layman Explanation

MAC Address is like an Aadhaar Number for a network card.

No two NICs should have the same MAC Address.

---

# IP Address Architecture

### Formal Definition

An IP Address is a logical address assigned to a device for identification and communication on a network.

### Diagram

```text
Laptop
IP: 192.168.1.10
       |
       |
    Router
IP: 192.168.1.1
       |
       |
    Internet
```

### Layman Explanation

If MAC Address is your Aadhaar Number,

then IP Address is your current home address.

You may change houses (IP), but your Aadhaar (MAC) remains the same.

---

# TCP Communication Architecture

### Three-Way Handshake

Before communication starts, TCP establishes a connection.

### Diagram

```text
CLIENT                      SERVER

  SYN -------------------->

      <---------------- SYN + ACK

  ACK -------------------->

Connection Established
```

### Explanation

Step 1:
Client asks,
"Can we communicate?"

Step 2:
Server replies,
"Yes, I am ready."

Step 3:
Client confirms,
"Great, let's start."

Now data transfer begins.

### Layman Example

Like making a phone call:

Person A: Can you hear me?

Person B: Yes, I can hear you.

Person A: Great.

Conversation starts.

---

# UDP Communication Architecture

### Diagram

```text
CLIENT                      SERVER

DATA -------------------->

DATA -------------------->

DATA -------------------->

No Confirmation
```

### Explanation

UDP simply sends data.

No acknowledgement.

No retransmission.

### Layman Example

Like a radio station broadcasting news.

The station does not check whether everyone received the message.

---

# Star Topology Architecture

### Diagram

```text
             PC1
              |
              |
PC2 ------ Switch ------ PC3
              |
              |
           Server
```

### Advantages

* Easy to manage
* Easy troubleshooting
* Most commonly used

### Disadvantages

* Switch failure affects the network

---

# Bus Topology Architecture

### Diagram

```text
PC1 ---- PC2 ---- PC3 ---- PC4
```

### Advantages

* Low cost

### Disadvantages

* Single cable failure affects the entire network

---

# Ring Topology Architecture

### Diagram

```text
     PC1 ------ PC2
      |          |
      |          |
     PC4 ------ PC3
```

### Advantages

* Predictable communication

### Disadvantages

* One failure can affect the ring

---

# Mesh Topology Architecture

### Diagram

```text
      PC1
     / | \
    /  |  \
 PC2---|---PC3
    \  |  /
     \ | /
      PC4
```

### Advantages

* Highly reliable
* Multiple paths available

### Disadvantages

* Expensive
* Difficult to maintain

---

# Data Communication Flow

### How Google Opens

```text
Browser
   |
   |
DNS Query
   |
   |
DNS Server
   |
Returns IP Address
   |
   |
Router
   |
   |
Internet
   |
   |
Google Server
```

### Real Example

When you type:

[www.google.com](http://www.google.com)

The browser does not understand the name.

DNS converts:

[www.google.com](http://www.google.com)

into something like:

142.250.183.110

Then communication begins.

---

# Quick Interview Definitions

### Network

A collection of interconnected devices that communicate and share resources.

### NIC

A hardware component used to connect a device to a network.

### MAC Address

A unique hardware identifier assigned to a NIC.

### IP Address

A logical address used to identify devices on a network.

### Protocol

A set of rules governing communication between devices.

### TCP

A reliable, connection-oriented protocol that guarantees delivery.

### UDP

A fast, connectionless protocol that does not guarantee delivery.

### Topology

The physical or logical arrangement of devices in a network.
