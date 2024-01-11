---
title: "Course Notes: Computer Networking"
date: 2023-02-22T18:30:00+05:30
toc: true
toc_label: "Notes"
---

This is the summary of what I learned from Kunal Kushwaha's YouTube Course on Computer Networking.

Kunal's Video:

{% include video id="IPvYjXCsTg8?si=AmH6JDJ9RZdTg5QK" provider="youtube" %}

# What is Computer Network?

Computers connected together form a Computer Network.

# What is Internet?

Connection of computer networks on a global scale is called Internet.

## How it was developed?

ARPA (Advanced Research Projects Agency) developed **ARPANet** to communicate between the fascilities in MIT, Stanford, UCLA and University of Utah. They used TCP/IP communication protocol.

Later, a **World Wide Web** was developed, that held all the files which were accessible by their web links. This was among the first websites to be developed: 

[](http://info.cern.ch/hypertext/WWW/TheProject.html)

**The Internet Society** maintains the protocols and set of rules used for the Internet.

# Protocols

- Transmission Control Protocol (TCP)
    - Hyper Text Transfer Protocol (HTTP)
- User Datagram Protocol (UDP)

# IP Addresses | Port Numbers

Our computers, mobile phones are connected to the internet via our modem. Our modems have a Global IP address, which is assigned by the **Internet Service Provider (ISP)**. So, if you check any connected device’s IP, all the devices connected to the same modem will have the same global IP address. However, the modem assigns each device a unique local IP address. It does this using **Dyanamic Host Configuration Protocol (DHCP)**. 

So if someone from your network tries to access Google, it will only see the Global IP address. The modem then sends the data returned from Google to the specific device using **Network Access Translator (NAT).** 

IP addresses decide which device the data is sent to. However, the **Port Number** decides which application the data is sent to. For eg. on your computer you have Chrome and WhatsApp open, the port number is the one which decides whether the image that was sent to your IP address was for Chrome or for WhatsApp.

There are around $2^{16}$ port number present for each modern device. However, some ports are already assigned. For eg. port 80 is assigned for HTTP. Port number 0 - 1023 are reserved ports. 1024 - 49152 are registered for various applications. The remaining ones are available for the user.

# Connections

- The internet speed is in bits per second… 8-bits = 1 byte. The ISP decides your internet speed.
- There are two types of ways data is passed over the network - the guided way and an unguided way.
- The networks are connected using undersea cables. The map is found here:

[Submarine Cable Map](https://www.submarinecablemap.com/)

## Metropolitan Area Network (MAN)

Across a City

## Wide Area Network (WAN)

Across countries

Connected via Optical Fiber Cables

**WAN + MAN + LAN form the internet**

- SONET = Synchronous Optical Networking (for WAN to WAN)
- Frame Relay (for LAN to MAN/WAN)

## Modem

It is used to convert digital signals into analog signals and vice versa.

## Router

A device that routes the internet packet to the respective IP address.

# Topologies

- Bus Topology
- Ring Topology
- Star Topology
- Tree Topology
- Mesh Topology

# OSI Model (Open Systems Interconnection)

- **Application Layer**: It is implemented in software. You send the data from application layer to the presentation layer. It will be in the form words, characters, numbers etc.
- **Presentation Layer**: Presentation translated the data from application layer to binary and EBCDIC. It encodes, encrypts and compresses the data here. It also provides abstraction. SSL Protocols is used here.
- **Session Layer**: The session layer protocols helps in setting up and managing the connections and it enables the sending/receiving of data , followed by termination of the session. Authentication, Authorization takes place here.
- **Transport Layer**: UDP/TCP protocols are used here. Three things takes place here:
    - Segmentation: the data received from the session layer is divided into small parts called segments. Each segment will hold the source’s and destination’s port number and a sequence number. Sequence number helps to reassemble the segments in the correct order.
    - Flow Control: Transport layer decides how much data is being transferred. If there are internet speed difference between server and client, it will control the flow to send data properly.
    - Error Control: It adds a checksum to every data sent, and checks if data losses have occured.
    
    Connection Oriented Transmission - TCP [It is used in Email, File Transfer Protocol and more, it slower than UDP, but more robust, the transmissions by the sender receive acknowledgments from the receiver]
    
    Connectionless Oriented Transmission - UDP [UDP used in video conferencing and gaming, as it is faster, but it doesn’t have acknowledgements like TCP, which make it prone to data loss]
    
- **Network Layer**: Here communication happens with other networks. Here the router is present. This layer’s function is Logical Addresing. It adds the senders and receivers IP addresses to the the data segment and forms an IP packet. It performs routing based on IP addresses. And Load Balancing also takes place here.
- **Data Link Layer**: It allows you to directly communicate with the hosts. The physical addressing is done here. MAC adresses are used here. **Frame** is the data unit of a data link layer.
- **Physical Layer**: This is the actual hardware like wires which transmits the bits using electrical signals.

# TCP/IP Model (Internet Protocol Suite)

- **Application Layer**: Users interact with the network here. eg. WhatsApp, Google Chrome, etc.
    
    Protocols Used in Application Layer : HTTP, DHCP, FTP, SMTP, POP3, IMAC, SSH, VNC
    
    Other Protocls : Telnet - Terminal Emulation over Port 23, UDP (stateless connection)
    
    Sockets: It is the interface between the process and the internet. It is a gateway between the application and the network.
    
    Ports: Ephemeral Ports - If another application is using a required port, a new port number will be assigned to the current application, and will be deleted once the application receives the data. Ephemeral Ports can exist only on the client side and not on the server side.
    
    HTTP uses TCP. HTTP is a stateless protocol. The server doesn’t know the state of an HTTP request.
    
    HTTP Methods:
    
    - GET
    - POST
    - PUT
    - DELETE
    
    HTTP Status Codes Categories:
    
    - 1XX - Information
    - 2XX - Success
    - 3XX - Redirecting
    - 4XX - Client Error
    - 5XX - Server Error
    
    HTTP Special Codes:
    
    - 200 - Everything OK
    - 404 - URL not found
    
    Cookies: Unique string which is stored in the client’s browser. eg. Cart information is stored even if you have not created an account on the E-Commerce site. It is done so by using a Cookie. The server will have a cookie ID associated with your session stored in the database, when you login again to the website, it will fetch the details from the database, and show you your previously saved items in the cart.
    
    Third Party Cookies : Cookies which are set for the website you have not visited. e.g. On Facebook you see an Amazon advertisement, here even Amazon will get your cookie details, and will be able to track you accross the sites you visit.
    
    Simple Mail Transfer Protocol : Sender will send mail through sender’s SMTP server and sends it to receiver’s SMTP server. When the reciever logs in to his account he will download the email from receiver’s SMTP server.
    
    POP3 - Post Office Protocol : Uses port 110. It is used to download emails. Client connects to the POP server, sends a authorisation request, and the POP server replies with a ‘transact’ response and then the client is able to view the downloaded mails on his system.
    
    IMAP - Internet Message Access Protocol : Allows mails sync between different devices. e.g. If a mail is deleted on Mac, it will be deleted in iPhone, iPad etc. 
    
- **Transport Layer**: It takes the data from Network layer and sends it to the application, and vice versa. It works on the systems itself. e.g. You are chating on whatsapp, having a video call and downloading a file from the interent. These three different application’s data is received on the network. The transport layer sends the data packets to each application. It uses sockets and port numbers. Transport layer also takes care of congestion control.
Transport layers also calculates the checksums for packets to ensure packet integrity.
Timers are also present in this layer. If a packet is not acknowledged, it understands that it has been lost and retransmits it.
Each packets have unique sequence numbers which allows the transport layer to generate a complete data from the packets.
    
    **User Datagram Protocol (UDP)**: Here data may or may not be delivered, and data may change and data may not be in order. It is a connectionless protocol. UDP uses checksum, but doesn’t do anything about it. A header of 8 bytes is added to the data in UDP. This header contains the source port number (2 bytes), destination port number (2 bytes), length of the datagram (2 bytes), checksum (2 bytes). The complete packet size is $2^{16}$ bytes. Therefore size of data is $2^{16}-8$ bytes. UDP is faster than TCP. Use cases: Video conferencing apps, Gaming, etc.
    
    **Transmission Control Protocol (TCP)**: Application layer sends raw data, and TCP segments this data and divides into chunks and adds headers. It may also collect the data from network layer. It is used in HTTP, SMTP. When data does not arrive, it works on retransmission. And maintains the order of the data using sequence numbers. This is connection-oriented protocol. It has error control and congestion control. TCP is a full duplex connection. The packets also have acknowledgement numbers.
    
    **Three-way handshake:** The client first sends a SYN flag to establish a new connection with the server. The server acknowledges this request with a ACK flag. Once the client recieves this acknowledgment, it sends an ACK from its side, and completes the connection. Now, it can send data. 
    The sequence number is a random number, i.e. it does not start from 1 or 0. The randomness is for security reasons. Otherwise the hackers can easily make out the data from the sequence numbers. 
    An acknowledgment number (= sequence number + 1) is sent back from the server to acknowledge that data is recieved.
    
- **Network Layer**: This layer takes care of the movement of data from one device to another. It works with routers. Every router has its own Network Address. Each router has a routing table and a forwarding table. Using hop-by-hop forwarding, a client is connected to the server using routers.
e.g. 192.168.2.30 is an IP address… out of these, first three numbers constitutes the network address - 192.168.2 and the last one is the device address 30.
In the network layer, there is a ‘Control Plane’ that forms these routing and forwarding tables. Routers store these datas as graphs.
Two types of routing techniques - Static Routing: Everything is added manually in the routing table; Dynamic Routing: It dynamically adds routes in the routing table.
Algorithms like Bellman-Fords, Djikstra, etc are used in routing. They can find the shortest available path between the client and the server.
    
    Network Layer Protocol = Internet Protol (IP)
    
    IPv4 : 32 bit, 4 words
    
    IPv6 : 128 bit
    
    All routers are not interconnected… i.e. your and your neighbours routers are not directly connected. Our routers are conencted to the ISP routers. The ISP routers hold the data of routing tables and forwarding tables. The ISP also doesn’t hold the data of all addresses, it holds blocks of addresses using Subnets. When router wants to connect to another IP, it uses the destination’s  subnet ID. 
    e.g. 192.168.2.30 is an IP address… out of these, first three numbers constitutes the subnet ID - 192.168.2 and the last one is the host ID 30.
    
    There are different classes of IP addresses: Class A (0.0.0.0 to 127.255.255.255), Class B (128.0.0.0 to 191.255.255.255), Class C (192.0.0.0 to 223.255.255.255), Class D (224.0.0.0 to 239.255.255.255), Class E (240.0.0.0 to 255.255.255.255).
    
    Subnet Masking allows to mask a few bits. eg. 24 bits are masked, then IP addressses for 192.0.1.0 can take values from 192.0.1.0 to 192.0.1.255.
    
    IETF (Internet Engineering Task Force). They assign IP addresses based on region and ISPs. There are a few reserved addresses. eg. 127.0.0.1 is reserved for local host. This is also called loopback address i.e. a process can connect to its own device using this IP address.
    
    IPV6 has $2^{128}$ addresses. However, it is not backwards compatible. Hence it is still not majorly in use, as it would require an upgrade of all ISPs and other hardware.
    
    Middleboxes: These devices interact with the IP packets. Examples:
    
    - Firewall: It filters IP packets based on various rules. They change the values in the header and can change the parameters of the IP packet. There are two kinds of firewalls - stateless and stateful firewalls. Stateful firewall is more efficient.
    - Network Address Translation (NAT): It is a method of mapping an IP address space into another by modifying network address information in the IP header of packets.
- **Data Link Layer**: It sends the data over physical medium. Devices connected in LAN have different data link layer addresses. When a device wants to connect over other device on the same LAN it will check it’s ARP (Address Resolution Protocol) cache if it has that device’s data link layer address.
    
    The data link layer frame consists of the Data Link layer address of the sender and the IP address of the receiver. The Data Link Layer address is the MAC address of the component. Each component like Bluetooth, WiFi have different MAC addresses. 
    
    The Data Link Layer also does framing and does error correction.
    
- Physical Layer

If you compare it with OSI model, here the application, presentation and session layers are merged into a single application layer. OSI model is theoritical whereas TCP/IP model is in practice.

The data is called differently at every stage of the protocol. In transport layer it is called a ‘segment’. In network layer, it is called a ‘packet’ and in the the data link layer it is called a ‘frame’.

In a packet, the header is of 20 bytes. It has IP version, length, identification number, flags, protocols, checksum, addresses, etc. It also contains Time to Live (TTL): The time till the packet is active.

# Types of Server Architecture

- Client-Server Architecture: A client sends a ****************request**************** to the server, and the server sends a ****************response**************** to the clients request.
- Peer-to-Peer Architecture: It is a decentralised network. eg. BitTorrent

# DNS (Domain Name System)

When you write ‘google.com’ in the browser, the DNS gets the respective IP address from it’s database and connect you to that server.

If you’re connecting to [mail.google.com](http://mail.google.com) Here, ‘com’ is a top-level domain, ‘google’ is a second-level domain, ‘mail’ is the sub-domain. This means that you’re connecting to the mail application of Google.

Top-Level Domain connects to the Root DNS Servers. Other examples of TLD: .org, .io, .com, etc. These are the first point of contact.

You can view the root DNS servers here: 

[Root Server Technical Operations Association](https://root-servers.org/)

These top level domains are registered by ICANN.

Steps while connecting to a website:

1. The browser checks in it’s own cache, if it has the IP address stored for the given URL.
2. If it is not able to find it, it will ask the ISP’s local DNS server for the IP address. Note: Even if you use incognito, your local ISP server will have the details about the sites you visit as per your DNS requests. And as per law, they can reveal your DNS requests when requested legally.
3. If it is not found in ISP’s local DNS server, it is checked in the Root DNS server.
4. If it is not found in Root DNS server, it is asked to the TLD server, and it will connect you to the respective server.

You can only rent a domain name, and not buy it permanently.

You can use `dig` command (Domain Information Groper) to view the DNS details of a particular URL. e.g. `dig [google.com](http://google.com)` in terminal. To view more information about the command use `man dig`
