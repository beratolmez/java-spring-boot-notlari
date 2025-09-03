# Computer Networks

## Chapter 1: The Internet and Network Core

### What is the Internet?

The internet is a vast collection of interconnected devices that communicate with each other. Devices connect to routers, which forward data via transmission media (cables, radio waves, etc.) to other routers and devices. The largest network of these smaller networks is what we call the internet.

* **Protocols:** These define the format, order, and actions for messages sent and received between devices.
* **Network Edges:** These are the client and server devices, with servers often located in large data centers.
* **Physical Media:** Communication links can be wired (cables) or wireless (radio waves).
* **Network Core:** This consists of routers that form the "network of networks."

### Accessing the Network

Many devices connect to a central unit, which carries traffic to the network core.

* **Frequency Division Multiplexing (FDM):** Different frequency bands are used to carry different channels.
* **Digital Subscriber Line (DSL):** Voice and data travel on different frequencies. A multiplexer directs voice traffic to the telephone network and data to the internet service provider.

### Sending Data Packets

A host breaks down an application message into smaller units called **packets**.
* The length of a packet is denoted by **L** (in bits).
* The transmission rate (bandwidth) is denoted by **R** (in bits per second).

### Delays
* **Transmission Delay:** The time it takes to push all of a packet's bits onto the link.
    * Formula: `L / R`
* **Propagation Delay:** The time it takes for a bit to travel from one end of the physical link to the other.
    * Formula: `d / s` (physical link length / propagation speed)

---

## Chapter 2: Application Layer

### Sockets

Processes receive and send messages through **sockets**. Sockets are an interface between the application layer and the transport layer.

### Transport Protocols

* **TCP (Transmission Control Protocol):** A reliable, connection-oriented protocol. It ensures that data is delivered in order and without loss. It uses acknowledgments and retransmissions.
* **UDP (User Datagram Protocol):** A fast but unreliable, connectionless protocol. Packets may be lost or arrive out of order. It's used for applications that prioritize speed over reliability, such as streaming.

### HTTP (Hypertext Transfer Protocol)

HTTP is the application layer protocol for the web. It uses **TCP** for reliable data transfer.

---

## Chapter 3: Transport Layer

The transport layer is responsible for segmenting messages from the application layer at the sender and reassembling them at the receiver.

### TCP Socket

A TCP socket is uniquely identified by a **4-tuple**:
* Source IP address
* Source port number
* Destination IP address
* Destination port number

### UDP (User Datagram Protocol)

* **No Handshake:** UDP does not perform a connection handshake. This makes it fast but unreliable.
* **Use Cases:** DNS, SNMP, and real-time multimedia applications.

### Reliable Data Transfer (rdt)

The **rdt** protocol ensures that packets are delivered reliably over an unreliable network. This is achieved by using mechanisms like:
* **Acknowledgements (ACKs):** The receiver sends an ACK to confirm it received a packet.
* **Negative ACKs (NAKs):** The receiver sends a NAK to indicate a packet was corrupted or lost.

### RDT 3.0 (Stop-and-Wait)

This is a specific rdt protocol. The sender sends one packet and waits for an ACK before sending the next.

* **Lossless Scenario:** The sender sends `packet0`, the receiver gets it and sends `ack0`, the sender receives `ack0` and sends `packet1`, and so on.
* **Lossy Scenario:** If a packet or an ACK is lost, a **timeout** mechanism triggers a retransmission.

### TCP Retransmission Scenarios

TCP uses sequence numbers and ACKs to handle packet loss and reordering.
* **Sequence Number:** A unique identifier for the first byte of data in a packet.
* **ACK Number:** The sequence number of the **next byte** the receiver is expecting.

* **Example:** If the sender sends a segment with sequence `92` and `8` bytes of data, the receiver, upon receipt, will send back an ACK of `100`.

---

## Chapter 4: Network Layer

### Data Plane vs. Control Plane

* **Data Plane:** The "local" function of a router that forwards packets from an input link to an output link.
* **Control Plane:** The "network-wide" logic that determines how packets are routed from a source to a destination.

### Subnet

A subnet is a logical subdivision of an IP network. Devices within the same subnet can reach each other physically without an intervening router.

---

## Exam Topics

#### Midterm

* RDT 3.0 and Stop-and-Wait Operation
* TCP Sequence Numbers and ACKs (e.g., calculating ACK values)
* TCP Retransmission Scenarios (e.g., what ACK value is sent when a packet is lost)
* Timeout and Duplicate ACKs

#### Final

* Focus on the Transport, Network, and Link layers.
* One double-sided reminder sheet is allowed.