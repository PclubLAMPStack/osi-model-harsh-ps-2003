## Computer Networking

# Devices
Devices such as switches, routers, and access points form the foundation of computer networks. Switches connect and help to internally secure computers, printers, servers, and other devices to networks in homes or organizations. Access points are switches that connect devices to networks without the use of cables. Routers connect networks to other networks and act as dispatchers. They analyze data to be sent across a network, choose the best routes for it, and send it on its way. Routers connect your home and business to the world and help protect information from outside security threats. While switches and routers differ in several ways, one key difference is how they identify end devices. A Layer 2 switch uniquely identifies a device by its "burned-in" MAC address. A Layer 3 router uniquely identifies a device's network connection with a network-assigned IP address. Today, most switches include some level of routing functionality.
# Mac and IP 
MAC and IP addresses uniquely define devices and network connections, respectively, in a network. A MAC address is a number assigned to a network interface card (NIC) by a device's manufacturer (host id). A MAC address is 48 bits long and is commonly written as a sequence of 12 digit hexadecimal digits. The first six hexadecimal digits known as the Organizational Unique Identifier (OUI) which is assigned by the IEEE Standards Association identify the manufacturer. The last six digits represent the serial number of the device. The first six digits are. Consequently, every MAC address is unique. An IP address is a number assigned to a network connection. A MAC (Media Access Control) address is the physical hardware identifier for the actual network card itself; whereas, an IP address is a logical network address. A MAC address is permanently programmed into the hardware device by the manufacturer; therefore, a MAC address cannot be changed. An IP address can be changed.
Public IP addresses are issued by your Internet Service Provider. Private IP addresses can be issued automatically by your router or set manually (either directly on your computer, or within the routers administration panel). Unless otherwise specified, your router most likely uses DHCP to allocate IP addresses automatically.
Whether public or private, IP addresses are assigned in blocks and these blocks differ in size. The size of the block assigned is written after a forward slash (/), also known as an oblique. The oblique tells us the number of IP addresses contained in that block. For example, a private network address “192.168.1.1/24” has 256 host addresses. These host addresses are the logical IP addresses that are necessary to connect your computer to the Internet. The number 24 refers to how many bits are contained in the network; therefore, it is from this number that the address space is calculated. It can be calculated mathematically, but it’s easier to use a CIDR chart.
http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing
Different network hardware manufacturers (ASUS, Linksys, NetGear, D-Link, etc.) use different IP address configurations but private IP addresses within a LAN always start with:

10.x.x.x
172.16.x.x
192.168.x.x
The reason they always start with one of the above numbers is because these IP’s have been reserved globally for Local Area Networks only. For the sake of simplicity, we’ll stick with 192.168.x.x from this point forward. This is the most common IP address configuration among consumer line products. 10.x.x.x is typically more suitable for businesses that require large blocks of IP addresses.
Internet Service Providers issue either static or dynamic public IP addresses. Commercial customers with business accounts typically receive a static public IP address that does not change.
Residential customers are typically issued a dynamic IP address that can change at anytime. However, due to the demand of IP addresses world-wide (and to prevent IP address exhaustion), these days ISP’s often use what’s called sticky IP’s for residential customers. Sticky IP’s are still dynamic by definition, but rarely do they actually change.
Why would I want a static public IP address?
Imagine for a moment that you are traveling out of town and you want to access a device on your home network. If your ISP changes your public IP address frequently (dynamically), you may be able to reach your network one day, and a few days later (if the public IP address changes), you’ll be unable to reach your network. This would be the equivalent of your cell phone number changing to a random number without your knowledge. There would be no way for people to reach you.
DHCP is a feature that issues IP addresses dynamically to computers within your network. The challenge with using both static IP addresses and dynamic IP addresses within the same network, is that the router can sometimes issue an IP address automatically that conflicts with, or matches an IP address that you set manually. Thankfully, there is an easy way around this problem –by defining what’s called an “IP address pool.” By defining an IP address pool, you are essentially creating a pool of IP addresses available for the router to choose from.
For example:

IP address pool: 192.168.1.100 ~ 192.168.1.199

Using the IP address pool above, the router will “dynamically” issue IP addresses between x.x.x.100 and x.x.x.199. This way, you can reserve your static IP addresses somewhere at x.x.x.99 or below. The beauty here is the flexibility and control you have over your network.
Accessibility to the server is determined by whether or not it has a public IP address or private IP address. If the server has a public IP address, it can be accessed from the web. If it has a private IP address, it can only be accessed from inside of your LAN (unless you setup port forwarding for remote access).

By default, the IP address pool is between 1 and 254. Why? Because x.x.x.255 is a broadcast address. The broadcast address always ends in 255. Also notice that all of the IP addresses begin with 192.168.1.x. This is because you need an address pool for each subnet. So if you ever decide to separate your business computers from your work computers, you can create a new subnet and new IP address pool for that subnet.
A broadcast address is an address that allows information to be sent to all devices in a network, rather than a specific machine. Therefore, the broadcast address for 192.168.1.0 is 192.168.1.255.

Why can’t I visit websites after changing my IP address?
Have you rebooted your router and your computer? If so, you may need to flush your DNS resolver cache. Remember when we changed the IP address, we also set the DNS server to use the IP address of the router. As a result, your computer could still be looking for the old settings.

You may have noticed that each device within the LAN has an IP address that begins with 192.168.1.x. You may have also noticed that the router has two IP addresses, one on each side of the dotted line, which leads us to the following question:

Why does a router have two IP addresses?
That’s a great question! And while it deserves a somewhat long (and rather geeky) answer, there is no need to worry – this will be painless, I promise.

You see, in the corporate world, businesses use what is known as a Network Address Translation (NAT) server; whereas, most small businesses and residential homes use a router. Essentially, they do the same thing, only a router does it on a smaller scale.

The reason the router has two IP addresses, is because there are two types of IP addresses; public and private. In the illustration above, everything in the Wide Area Network (WAN) has a public IP address. Everything on the Local Area Network (LAN) has a private IP address.

For now, think of public IP addresses as a primary phone number of a large corporation. Think of private IP addresses like telephone line extensions.

A Public IP address is designed for public access and is accessible by anyone on the Internet. When you visit a website, that website is hosted on server that is associated with a public IP address.

A Private IP addresses is used only within your LAN. Therefore, no one can reach your computers private IP address from outside of your Local Area Network.

All traffic coming inbound to your private network (your LAN), must first come through a public IP network address. As a result, anyone can reach the public IP address of your router (on the WAN side) because, well, . . .this is a public IP address! The objective is to hide your private Local Area Network (LAN) behind one single public IP address. This process requires a gateway/router. This is where a NAT server comes into the picture.

# NAT
NAT Servers (routers) have three primary functions:

They route the call to the proper computer.
They privatize devices connected to your LAN. Hence the term “private IP.”
They control the type of traffic by directing it through the proper portal (opening).
Since traffic goes in multiple directions (into your LAN, out of your LAN, and within your LAN), the router is charged with the task of making sure that the computer or device that made the outbound call (the request) is the same computer that receives the inbound response.

Computers within your local network can communicate freely. However, traffic coming into your LAN or going out of your LAN requires a technology called Network Address Translation (NAT). NAT allows your computers with private IP addresses to access the public space of the Internet.

Were you born before 1975? Do you remember the days when we had to use telephone operators? Think of a router like a telephone operator.

Here’s how NAT works:
The NAT server (router) takes the outbound call from a computer connected to your LAN, say, your laptop computer . . .

It puts the call request in its memory.
It then converts the private IP address to its own public IP address and forwards the request.
When a response is returned from the Internet, it searches its memory to see which device made the call and then delivers the packet to the proper computer.
As a result, all outbound requests to the Internet appear as if they’re coming from one public IP address.
NAT makes it appear as though every device behind your router is using the same public IP address; when actually, each device within your LAN has its own private IP address.

Additionally, in order to get information from the WAN to your LAN, and to-and-from computers within your LAN, your router must allow traffic to pass through a portal (an opening) in the routers firewall. Different programs use different port numbers. In order for programs to send/receive data through a port in your router, the router must allow it to happen. Opening a port is known as port forwarding.
# DNS
Domain Name System(DNS) is a hostname for IP address translation service. DNS is a distributed database implemented in a hierarchy of name servers. It is an application layer protocol for message exchange between clients and servers. It is required for the functioning of the Internet.

Every host is identified by the IP address but remembering numbers is very difficult for people also the IP addresses are not static therefore a mapping is required to change the domain name to the IP address. So DNS is used to convert the domain name of the websites to their numerical IP address.The working of DNS starts with converting a hostname into an IP Address. A domain name serves as a distinctive identification for a website. It is used in place of an IP address to make it simpler for consumers to visit websites. Domain Name System works by executing the database whose work is to store the name of hosts which are available on the Internet. The top-level domain server stores address information for top-level domains such as .com and .net, .org, and so on. If the Client sends the request, then the DNS resolver sends a request to DNS Server to fetch the IP Address. In case, when it does not contain that particular IP Address with a hostname, it forwards the request to another DNS Server. When IP Address has arrived at the resolver, it completes the request over Internet Protocol. 

Why DNS uses UDP instead of TCP?
DNS primarily uses the User Datagram Protocol (UDP) on port number 53 to serve requests. DNS queries consist of a single UDP request from the client followed by a single UDP reply from the server. When the length of the answer exceeds 512 bytes and both client and server support EDNS, larger UDP packets are used. Otherwise, the query is sent again using the Transmission Control Protocol (TCP). TCP is also used for tasks such as zone transfers. Some resolver implementations use TCP for all queries. 
Another reason DNS uses UDP is because it is a connectionless protocol, meaning that it does not establish a dedicated end-to-end connection before sending data. This makes it more suitable for DNS queries, which are often short and require quick responses. In contrast, TCP is a connection-oriented protocol, meaning it requires a more complex process to establish a connection before data can be transmitted.
Additionally, because DNS is a widely used protocol, there is a significant amount of traffic that needs to be handled by DNS servers. UDP is more scalable and efficient than TCP for handling large amounts of traffic, as it does not require the overhead of connection management
There are the following interesting facts about TCP and UDP on the transport layer that justify the above. 
1. UDP is much faster. TCP is slow as it requires a 3-way handshake. The load on DNS servers is also an important factor. DNS servers (since they use UDP) don’t have to keep connections. 
2. DNS requests are generally very small and fit well within UDP segments. 
3. UDP is not reliable, but reliability can be added to the application layer. An application can use UDP and can be reliable by using a timeout and resend at the application layer.
To prevent DNS Spoofing Response Rte Limit, DNS Filtering Monitoring and Analysis is used. 
# How data is managed through routers?
When you router wants to send data packets to your computer with IP address ‘X’, the router needs to know what your computers MAC address is. So, the router sends an ARP broadcast request on the LAN. ARP means Address Resolution Protocol. Your router is basically trying to resolve (find) the physical address of which computer this IP address belongs to. So, the router sends a broadcast that says “hey everyone, if you have IP address X, please tell me what your MAC address is.” One of your computers will respond “Hello, I have IP address X and my MAC address is XYZ, please forward the data to my MAC address.”

The IP address is what is first used to find the right network. Once the request reaches the correct network using the IP address, ARP is what converts an IP address to a MAC address and delivers the data packet to the right computer.

Note: ARP may sound similar to a Network Address Translation (NAT), but you need to understand that NAT is used for addressing and locating networks; whereas, ARP is used to deliver the actual data to the physical device.

# SubNet
A Subnet is a subnetwork of computers, partitioned from a larger computer network (such as the Internet). A subnet represents all of the devices within a LAN, including all client, server, and host computers within that group. One benefit of creating a subnet is that it allows different computer groups to be connected to the Internet using a single shared public IP address. Each router has it’s own private LAN IP address. But they can share one single public WAN IP address. 
Subnets can be separated physically using hardware. The other type is separated virtually. Virtual separation can be achieved using the firmware installed on your router or switch. This is known as a Virtual Local Area Network (VLAN).

# HTTP vs HTTPS
Hypertext Transfer Protocol (HTTP) (port 80) is a protocol using which hypertext is transferred over the Web. Due to its simplicity, HTTP has been the most widely used protocol for data transfer over the Web but the data (i.e. hypertext) exchanged using HTTP isn’t as secure as we would like it to be. Cryptographic protocols such as SSL and/or TLS turn HTTP into HTTPS (port 443) i.e. HTTPS = HTTP + Cryptographic Protocols. HTTP works on Application Layer whereas HTTPS works on Transport Layer. HTTPS is better than HTTP because HTTPS provides security. HTTP can also be hacked where as HTTPS cannot be hacked. HTTP does not help in search ranking whereas HTTPS helps in search ranking. The speed of HTTP is faster than the speed of HTTPS. Due to the presence of SSL Protocol in HTTPS, the webpages become slower than HTTP.
# Visiting a Website
When you visit a web page, there are a number of things that determine how quickly the page loads:

*The speed of the server hosting that website
*How large the web page is (images, etc).
*How much bandwidth your ISP has allowed you
*How quickly your router can route data packets
*The speed of the Network Interface Controller on your computer.
So, bandwidth and latency play a huge role in the performance you experience between clients and servers.
The term bandwidth to describe the maximum bit rate of a system
When you hear someone say “My Internet speed is 30 Mbps” or something similar, what they are actually referring to is the bandwidth capacity of their Internet service, not the speed. The speed of a network is actually the result of bandwidth and latency. Bandwidth refers to how wide the data pipe is, not how fast the data is transferred. The transfer rate is measured in latency. And latency means “delay.” So speed and bandwidth work together. The wider the pipe is, the less delay you’ll experience when loading webpages and transferring files. This is one reason you don’t want people using your WiFi without your knowledge. if necessary, use a MAC address filter to slow down those unwanted freeloaders.
# Latency
Latency is the amount of time it takes a data packet to travel from point A to point B. Together, bandwidth and latency define the speed and capacity of a network. Latency is usually expressed in milliseconds and can be measured using a ping command from your computer.

When you run a ping command, a small packet of data (usually 32 bytes), is sent to another machine whereby the round-trip-time is measured in milliseconds. The ping command measures how long it takes for the data packet to leave the source computer, travel to the destination computer, and return back to the source computer.
# Bandwidth
Bandwidth is expressed in bits per second. It refers to the amount of data that can be transferred during one second. Obviously, the wider the pipe, the more bits can be transferred per second. And if your bandwidth is congested, your latency (delay) is increased. internet speed refers to the rate at which data can be transmitted, while the definition of bandwidth is the capacity for that speed. To use the water metaphor again, speed refers to how quickly water can be pushed through a pipe; bandwidth refers to the quantity of water that can be moved through the pipe over a set time frame. While bandwidth is traditionally expressed in bits per second (bps), modern network links now have far greater capacity, which is why bandwidth is now more often expressed as Mbps or Gbps.
Bandwidth connections can be symmetrical, which means the data capacity is the same in both directions -- upload and download -- or asymmetrical, which means download and upload capacity are not equal. In asymmetrical connections, upload capacity is typically smaller than download capacity; this is common in consumer-grade internet broadband connections. Enterprise-grade WAN and DIA links more commonly have symmetrical bandwidth.
Streaming and downloading is essentially the same thing as far as bandwidth is concerned. But Streaming Platforms use different system design architecture. //cover it
The maximum capacity of a network connection is only one factor that affects network performance. Packet loss, latency and jitter can all degrade network throughput and make a high-capacity link perform like one with less available bandwidth.

An end-to-end network path usually consists of multiple connections, each with different bandwidth capacity. As a result, the link with the lowest bandwidth is often described as the bottleneck because it can limit the overall capacity of all connections in the path.

Many enterprise-grade networks are deployed with multiple aggregated links acting as a single logical connection. If, for example, a switch uplink uses four aggregated 1 Gbps connections, it has an effective throughput capacity of 4 Gbps. However, if two of those links were to fail, the bandwidth limit would drop to 2 Gbps.

bandwidth on demand -- also called dynamic bandwidth allocation or burstable bandwidth -- is an alternative model that enables subscribers to increase the amount of available bandwidth at specific times or for specific purposes. Bandwidth on demand is a technique that can provide additional capacity on a communications link to accommodate bursts in data traffic that temporarily require more bandwidth.

Rather than overprovisioning the network with expensive dedicated links year-round, bandwidth on demand is frequently used in WANs to increase capacity as needed for a special event or time of day when traffic is expected to spike. An online flower retailer, for example, may only need to increase its capacity in the weeks leading up to Mother's Day. Bandwidth on demand enables enterprises to only pay for the additional bandwidth they consume over a shorter period of time.

Bandwidth on demand is available through many internet and WAN service providers. Depending on the network link a customer currently has in use, a provider may be able to provision additional capacity on demand using the existing connection. For example, a 100 Mbps link might be able to burst up to 1 Gb because the service provider's connection has available capacity. If a customer needed more than the absolute maximum bandwidth available on that link, another physical connection would be required.

Occasionally, a service provider will enable customers to burst above their subscribed bandwidth cap without charging additional fees. However, if customers were to regularly sustain more than 100 Mbps using the burst feature, they are commonly billed by the service provider using 95th percentile calculations.
DDNS (dynamic dns) takes a domain name such as www.yourdomain.com and associates it with your public IP address. It also updates your public IP address at predefined intervals (say, every 7, 14, or 28 days). when your ISP gets a “wild hair” and decides to change your public IP address, the DDNS feature within the router will notify your domain name registrar (or DDNS service) and say, “Hey, we have a new IP address! Please send all traffic to my new IP address!”
The server will host a website for me. My server also has a web-based administration panel that I would like to access from anywhere. Additionally, I also need access to my desktop computer while I’m away. Therefore, I’ll need to configure three port forwarding rules: (1) one for the website, (2) one for the server admin panel, and (3) a remote desktop connection to my desktop computer.

For this reason, devices that depend on port forwarding should always have a static IP address. They should never rely on dynamic IP addresses.
In order for the server to host my website publicly for the Word-Wide-Web, the router must first allow internet requests to pass through port 80. To access my servers administration panel, the router must allow requests through port 5000. And finally, to access my desktop computer, the router must also allow a connection through port 3389.
Once port 80 is open on the router and it has been mapped to the IP address of the server, I can reach my website three different ways:
The first way, is from within my LAN by typing the private IP address into my browser (192.168.1.2). This method does not request DNS information from the Web. Therefore, the request never travels outside of my LAN.

The second way is to enter my public IP address (74.68.117.209). This method does send a request externally to the WAN. You can reach this address from the Bahamas.

And finally, the third method, using a domain name such as www.mydomain.com. This method also sends a request externally to the WAN. In this case, the browser requests DNS information from the Web and resolves my public IP address behind the scenes. What about the administration panel? For my particular server (Synology DS710+), the application that manages the server is called DSM (Disk Station Manager). The DSM software is a web-based application that uses port 5000. In order to reach the DSM, I must append the port number to the private IP address, the public IP address, or domain name, separated by a colon. With ports 80 and 5000 open on my router, I can now access my website and my server administration panel from inside of my LAN, or outside from the Internet. This gives me access to my home network at anytime, from anywhere in the world.

And finally, by mapping port 3389, I can now connect and use my desktop computer from anywhere in the world. I can access it on my local network, or from a remote location using the public IP address, or the domain name, followed by the port number.
# Jitter and Packets
Information is transported from your computer in data packets across the internet. They are usually sent at regular intervals and take a set amount of time. Jitter is when there is a time delay in the sending of these data packets over your network connection. This is often caused by network congestion, and sometimes route changes.

Essentially, the longer data packets take to arrive, the more jitter can negatively impact the video and audio quality.

This can be an annoyance when you’re using your computer for recreational purposes. It’s close to unbearable in a professional setting when you’re making a conference call or trying to connect to the team. Jitter can be the difference between a successful voice over internet protocol (VoIP) call and a disastrous, glitchy one. 

Packets consist of two portions: the header and the payload. The header contains information about the packet, such as its origin and destination IP addresses (an IP address is like a computer's mailing address). packets actually have more than one header, and each header is used by a different part of the networking process. Packet headers are attached by certain types of networking protocols. Packet headers go at the front of each packet. Routers, switches, computers, and anything else that processes or receives a packet will see the header first. A packet can also have trailers and footers attached at the end. Like headers, these contain additional information about the packet.

Only certain network protocols attach trailers or footers to packets; most only attach headers. ESP (part of the IPsec suite) is one example of a network layer protocol that attaches trailers to packets.
# Protocol
A protocol is a standardized way of formatting data so that any computer can interpret the data. Many different protocols make the Internet work. Some of these protocols add headers to packets with information associated with that protocol. At minimum, most packets that traverse the Internet will include a Transmission Control Protocol (TCP) header and an Internet Protocol (IP) header. IP (Internet Protocol) is a network layer protocol that has to do with routing. It is used to make sure packets arrive at the correct destination.

If you enter an IP address or corresponding domain name in your browser, the router forwards your request to the internet which connects you to the server. This means that if you enter 172.217.0.0, you will reach the Google homepage but the situation is different with 127.0.0.1. The requests to this address will not be forwarded to the internet. TCP/IP recognizes from the first block (127) that you don’t want to access the internet, you are calling yourself instead. This then triggers the loopback. 
# TCP/IP
Web applications use HTTP protocol which is a layer over TCP protocol. Whereas internet applications can use either TCP or UDP protocol. The process of communication between devices over the internet happens according to the current TCP/IP suite model(stripped out version of OSI reference model).
TCP (Transmission Control Protocol) is one of the main protocols of the Internet protocol suite. It lies between the Application and Network Layers which are used in providing reliable delivery services. It is a connection-oriented protocol for communications that helps in the exchange of messages between different devices over a network. The Internet Protocol (IP), which establishes the technique for sending data packets between computers, works with TCP.

To make sure that each message reaches its target location intact, the TCP/IP model breaks down the data into small bundles and afterward reassembles the bundles into the original message on the opposite end.When a user requests a web page on the internet, somewhere in the world, the server processes that request and sends back an HTML Page to that user. The server makes use of a protocol called the HTTP Protocol. The HTTP then requests the TCP layer to set the required connection and send the HTML file.

Now, the TCP breaks the data into small packets and forwards it toward the Internet Protocol (IP) layer. The packets are then sent to the destination through different routes.

The TCP layer in the user’s system waits for the transmission to get finished and acknowledges once all packets have been received.
UDP is another protocol, which does not require IP to communicate with another computer.
 The Application layer is a top pile of a stack of TCP/IP models from where network referenced applications like web browsers on the client-side establish a connection with the server. From the application layer, the information is transferred to the transport layer where our topic comes into the picture. The two important protocols of this layer are – TCP, UDP(User Datagram Protocol) out of which TCP is prevalent(since it provides reliability for the connection established). However, you can find an application of UDP in querying the DNS server to get the binary equivalent of the Domain Name used for the website. 
TCP provides reliable communication with something called Positive Acknowledgement with Re-transmission(PAR). The Protocol Data Unit(PDU) of the transport layer is called a segment. Now a device using PAR resend the data unit until it receives an acknowledgement. If the data unit received at the receiver’s end is damaged(It checks the data with checksum functionality of the transport layer that is used for Error Detection), the receiver discards the segment. So the sender has to resend the data unit for which positive acknowledgement is not received. You can realize from the above mechanism that three segments are exchanged between sender(client) and receiver(server) for a reliable TCP connection to get established. 

TCP/IP follows connectionless a horizontal approach. OSI follows a vertical approach.
The Transport layer in TCP/IP does not provide assurance delivery of packets.	In the OSI model, the transport layer provides assurance delivery of packets.
Protocols cannot be replaced easily in TCP/IP model.	While in the OSI model, Protocols are better covered and are easy to replace with the technology change.
TCP/IP model network layer only provides connectionless services.	Connectionless and connection-oriented services are provided by the network layer in the OSI model.

TCP protocol has methods for finding out corrupted segments, missing segments, out-of-order segments and duplicated segments. 

Error control in TCP is mainly done through the use of three simple techniques : 

Checksum – Every segment contains a checksum field which is used to find corrupted segments. If the segment is corrupted, then that segment is discarded by the destination TCP and is considered lost.
Acknowledgement – TCP has another mechanism called acknowledgement to affirm that the data segments have been delivered. Control segments that contain no data but have sequence numbers will be acknowledged as well but ACK segments are not acknowledged.
Retransmission – When a segment is missing, delayed to deliver to a receiver, corrupted when it is checked by the receiver then that segment is retransmitted again. Segments are retransmitted only during two events: when the sender receives three duplicate acknowledgements (ACK) or when a retransmission timer expires. 
Retransmission after RTO: TCP always preserves one retransmission time-out (RTO) timer for all sent but not acknowledged segments. When the timer runs out of time, the earliest segment is retransmitted. Here no timer is set for acknowledgement. In TCP, the RTO value is dynamic in nature and it is updated using the round trip time (RTT) of segments. RTT is the time duration needed for a segment to reach the receiver and an acknowledgement to be received by the sender.
Retransmission after Three duplicate ACK segments: RTO method works well when the value of RTO is small. If it is large, more time is needed to get confirmation about whether a segment has been delivered or not. Sometimes one segment is lost and the receiver receives so many out-of-order segments that they cannot be saved. In order to solve this situation, three duplicate acknowledgement method is used and missing segment is retransmitted immediately instead of retransmitting already delivered segment. This is a fast retransmission because it makes it possible to quickly retransmit lost segments instead of waiting for timer to end.

# OSI-Models
OSI refers to Open Systems Interconnection.

The lowest layer of the OSI reference model is the physical layer. It is responsible for the actual physical connection between the devices. The physical layer contains information in the form of bits. It is responsible for transmitting individual bits from one node to the next.

Functions of physical layer :

Bit synchronization: The physical layer provides the synchronization of the bits by providing a clock. This clock controls both sender and receiver thus providing synchronization at the bit level.
Bit rate control: The Physical layer also defines the transmission rate i.e. the number of bits sent per second.
Physical topologies: Physical layer specifies how the different, devices/nodes are arranged in a network i.e. bus, star, or mesh topology.
Transmission mode: Physical layer also defines how the data flows between the two connected devices. The various transmission modes possible are Simplex, half-duplex and full-duplex.

Layer 2- Data Link Layer (DLL)
The data link layer is responsible for the node-to-node delivery of the message. The main function of this layer is to make sure data transfer is error-free from one node to another, over the physical layer. When a packet arrives in a network, it is the responsibility of the DLL to transmit it to the Host using its MAC address. 
The Data Link Layer is divided into two sublayers:  
  Logical Link Control (LLC)
  Media Access Control (MAC)
The packet received from the Network layer is further divided into frames depending on the frame size of the NIC(Network Interface Card). DLL also encapsulates Sender and Receiver’s MAC address in the header. 

The Receiver’s MAC address is obtained by placing an ARP(Address Resolution Protocol) request onto the wire asking “Who has that IP address?” and the destination host will reply with its MAC address.  

The Functions of the Data Link Layer

Framing: Framing is a function of the data link layer. It provides a way for a sender to transmit a set of bits that are meaningful to the receiver. This can be accomplished by attaching special bit patterns to the beginning and end of the frame.
Physical addressing: After creating frames, the Data link layer adds physical addresses (MAC addresses) of the sender and/or receiver in the header of each frame.
Error control: The data link layer provides the mechanism of error control in which it detects and retransmits damaged or lost frames.
Flow Control: The data rate must be constant on both sides else the data may get corrupted thus, flow control coordinates the amount of data that can be sent before receiving an acknowledgment.
Access control: When a single communication channel is shared by multiple devices, the MAC sub-layer of the data link layer helps to determine which device has control over the channel at a given time.
Note: 1. Packet in the Data Link layer is referred to as Frame. 
      2. Data Link layer is handled by the NIC (Network Interface Card) and device  drivers of host machines. 
      3. Switch & Bridge are Data Link Layer devices.

Layer 3- Network Layer
The network layer works for the transmission of data from one host to the other located in different networks. It also takes care of packet routing i.e. selection of the shortest path to transmit the packet, from the number of routes available. The sender & receiver’s IP addresses are placed in the header by the network layer. 

The Functions of the Network Layer 

Routing: The network layer protocols determine which route is suitable from source to destination. This function of the network layer is known as routing.
Logical Addressing: To identify each device on Internetwork uniquely, the network layer defines an addressing scheme. The sender & receiver’s IP addresses are placed in the header by the network layer. Such an address distinguishes each device uniquely and universally.
Note: 1. Segment in the Network layer is referred to as Packet. 
      2. Network layer is implemented by networking devices such as routers.  

Layer 4- Transport Layer
The transport layer provides services to the application layer and takes services from the network layer. The data in the transport layer is referred to as Segments. It is responsible for the End to End Delivery of the complete message. The transport layer also provides the acknowledgment of the successful data transmission and re-transmits the data if an error is found.

At the sender’s side: The transport layer receives the formatted data from the upper layers, performs Segmentation, and also implements Flow & Error control to ensure proper data transmission. It also adds Source and Destination port numbers in its header and forwards the segmented data to the Network Layer. 

Note: The sender needs to know the port number associated with the receiver’s application. 

Generally, this destination port number is configured, either by default or manually. For example, when a web application requests a web server, it typically uses port number 80, because this is the default port assigned to web applications. Many applications have default ports assigned. 

At the receiver’s side: Transport Layer reads the port number from its header and forwards the Data which it has received to the respective application. It also performs sequencing and reassembling of the segmented data. 

The Functions of the Transport Layer 

Segmentation and Reassembly: This layer accepts the message from the (session) layer, and breaks the message into smaller units. Each of the segments produced has a header associated with it. The transport layer at the destination station reassembles the message.
Service Point Addressing: To deliver the message to the correct process, the transport layer header includes a type of address called service point address or port address. Thus by specifying this address, the transport layer makes sure that the message is delivered to the correct process.
Services Provided by Transport Layer :
1. Connection-Oriented Service: It is a three-phase process that includes

Connection Establishment
Data Transfer
Termination/disconnection
In this type of transmission, the receiving device sends an acknowledgment, back to the source after a packet or group of packets is received. This type of transmission is reliable and secure.

2. Connectionless service: It is a one-phase process and includes Data Transfer. In this type of transmission, the receiver does not acknowledge receipt of a packet. This approach allows for much faster communication between devices. Connection-oriented service is more reliable than connectionless Service.

Note: 1. Data in the Transport Layer is called Segments. 
      2. Transport layer is operated by the Operating System. It is a part of the OS and communicates with the Application Layer by making system calls. 
      3. The transport layer is called as Heart of the OSI model. 

Layer 5- Session Layer
This layer is responsible for the establishment of connection, maintenance of sessions, and authentication, and also ensures security.

The Functions of the Session Layer

Session establishment, maintenance, and termination: The layer allows the two processes to establish, use and terminate a connection.
Synchronization: This layer allows a process to add checkpoints that are considered synchronization points in the data. These synchronization points help to identify the error so that the data is re-synchronized properly, and ends of the messages are not cut prematurely and data loss is avoided.
Dialog Controller: The session layer allows two systems to start communication with each other in half-duplex or full-duplex.
Note: 1. All the below 3 layers(including Session Layer) are integrated as a single layer in the TCP/IP model as the “Application Layer”. 
      2. Implementation of these 3 layers is done by the network application itself. These are also known as Upper Layers or Software Layers. 

Scenario
Let us consider a scenario where a user wants to send a message through some Messenger application running in his browser. The “Messenger” here acts as the application layer which provides the user with an interface to create the data. This message or so-called Data is compressed, encrypted (if any secure data), and converted into bits (0’s and 1’s) so that it can be transmitted.
Layer 6- Presentation Layer
The presentation layer is also called the Translation layer. The data from the application layer is extracted here and manipulated as per the required format to transmit over the network. 

The Functions of the Presentation Layer are 

Translation: For example, ASCII to EBCDIC.
Encryption/ Decryption: Data encryption translates the data into another form or code. The encrypted data is known as the ciphertext and the decrypted data is known as plain text. A key value is used for encrypting as well as decrypting data.
Compression: Reduces the number of bits that need to be transmitted on the network.
Layer 7- Application Layer
At the very top of the OSI Reference Model stack of layers, we find the Application layer which is implemented by the network applications. These applications produce the data, which has to be transferred over the network. This layer also serves as a window for the application services to access the network and for displaying the received information to the user. Application Layer	Helps in identifying the client and synchronizing communication.
Some important Application layer protocols are TELNET, FTP, SMTP, DNS, DHCP etc.

OSI model acts as a reference model and is not implemented on the Internet because of its late invention. The current model being used is the TCP/IP model. 

6	Presentation Layer	Data from the application layer is extracted and manipulated in the required format for transmission.	Message	                        –
5	Session Layer	Establishes Connection, Maintenance, EnsuresAuthentication, and Ensures security.	Message	Gateway
4	Transport Layer	Take Service from Network Layer and provide it to the Application Layer.	Segment	Firewall
3	Network Layer	Transmission of data from one host to another, located in different networks.	Packet	Router
2	Data Link Layer	Node to Node Delivery of Message.	Frame	Switch, Bridge
1	Physical Layer	Establishing Physical Connections between Devices.	Bits	Hub, Repeater, Modem, Cables
# Why OSI Model?
Nowadays, the TCP/IP model is more common than the OSI model but still, it is used as a theoretical concept used to relate different technologies in computer networks. Following are the reasons of OSI model still being relevant:

Identify threats: OSI model helps to identify threats across the entire network. It helps IT experts, to detect network issues occurring at any stage of the networking process and troubleshoot such issues. It is also used to conduct asset inventory and categorize assets and data of organizations using layers of the model and address vulnerabilities and security incidents within the network based on the layers that are being affected by these issues.
Data-centric security posture: It provides a framework for conducting an inventory of the organization’s resources and hence has a data-centric perspective that helps to identify the areas of data security risks within the network. It provides detailed information about each layer of the model and this information plays a critical role in choosing correct tools which give better data visibility within the right OSI layer. OSI model is also important for compliance within the network as it ensures controls within the network are developed according to the environment of the data.
Secure cloud adoption: The popularity of cloud computing has increased significantly over the past few years and many organizations are migrating to the cloud because of its benefits but cloud systems have certain security issues like data breaches, malware injection, insecure APIs, data loss, etc. OSI model is useful while migrating to the cloud as its data-centric perspective helps in understanding the data security risks that cloud adoption might bring to the network. This allows organizations to develop better strategies to decide about the types of cloud systems to adopt which can reduce these security concerns.
Secure cloud infrastructure:  OSI model prioritize the security of the network and hence can be used within cloud systems that are prone to different security issues like a data breach, malware injection, insecure APIs, data loss, etc. OSI model is versatile and can be applied in different ways to cloud infrastructure. It conducts an inventory of security resources and assets of the organization and is modified in such a way that it benefits the security program of the network.
Integration: The OSI model can be integrated with other models and frameworks, such as the ITIL (Information Technology Infrastructure Library) framework for IT service management. By using the OSI model as a reference point, organizations can develop more effective IT service management processes that take into account the complexities of modern networking environments.

ipv4 vs ipv6 - https://www.guru99.com/difference-ipv4-vs-ipv6.html#:~:text=IPv4%20is%2032%2DBit%20IP,is%20an%20alphanumeric%20addressing%20method.&text=IPv4%20uses%20ARP%20(Address%20Resolution,to%20map%20to%20MAC%20address.

# Supernet
Supernetting is the opposite of Subnetting. In subnetting, a single big network is divided into multiple smaller subnetworks. In Supernetting, multiple networks are combined into a bigger network termed as a Supernetwork or Supernet. 

Supernetting is mainly used in Route Summarization, where routes to multiple networks with similar network prefixes are combined into a single routing entry, with the routing entry pointing to a Super network, encompassing all the networks. This in turn significantly reduces the size of routing tables and also the size of routing updates exchanged by routing protocols. 

# AAA
AAA (Authentication, Authorization, Accounting) – 
AAA is a standard-based framework used to control who is permitted to use network resources (through authentication), what they are authorized to do (through authorization), and capture the actions performed while accessing the network (through accounting). 

 

Authentication – 
The process by which it can be identified that the user, which wants to access the network resources, valid or not by asking some credentials such as username and password. Common methods are to put authentication on console port, AUX port, or vty lines. 
As network administrators, we can control how a user is authenticated if someone wants to access the network. Some of these methods include using the local database of that device (router) or sending authentication requests to an external server like the ACS server. To specify the method to be used for authentication, a default or customized authentication method list is used. 

 

Authorization – 
It provides capabilities to enforce policies on network resources after the user has gained access to the network resources through authentication. After the authentication is successful, authorization can be used to determine what resources is the user allowed to access and the operations that can be performed. 
For example, if a junior network engineer (who should not access all the resources) wants to access the device then the administrator can create a view that will allow particular commands only to be executed by the user (the commands that are allowed in the method list). The administrator can use the authorization method list to specify how the user is authorized to network resources i.e through a local database or ACS server. 

 

Accounting – 
It provides means of monitoring and capturing the events done by the user while accessing the network resources. It even monitors how long the user has access to the network. The administrator can create an accounting method list to specify what should be accounted for and to whom the accounting records should be sent. 
 
AAA implementation: AAA can be implemented by using the local database of the device or by using an external ACS server. 

 

local database – If we want to use the local running configuration of the router or switch to implement AAA, we should create users first for authentication and provide privilege levels to users for Authorization. 
 

ACS server – This is the common method used. An external ACS server is used (can be ACS device or software installed on Vmware) for AAA on which configuration on both router and ACS is required. The configuration includes creating a user, separate customized method list for authentication, Authorization, and Accounting. 
The client or Network Access Server (NAS) sends authentication requests to the ACS server and the server takes the decision to allow the user to access the network resource or not according to the credentials provided by the user. 
 

Note – If the ACS server fails to authenticate, the administrator should mention using the local database of the device as a backup, in the method list, to implement AAA.