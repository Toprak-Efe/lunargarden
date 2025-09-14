# Internet
## Views
There are different view paradigms on how to define the internet that operate on and through different abstraction layers, these are:
- Nuts and Bolts View
- Service View
- System View
### Nuts and Bolts View
#hosts #end-systems #links #routers #switches #bandwidth 
The internet is an information web of *hosts* connected by *communication links* where the flow of data is managed by **packet switches**.
#### Hosts
> [!DEFINITION] Hosts
> A host means an end-system which can be any device connected to internet such as PCs, laptops, tablets, servers, phones, toasters, etc.
#### Communication Links & Packet Switches
> [!DEFINITION] Communication Links & Packet Switches
> Communication links are different connection apparatus, such as fiber optic, copper cabling, radio transmission, and satellite links.
> 
> **Packet switchers** are devices that forward packets (chunks of data) from incoming links through the appropriate outgoing links to make precise interhost communication possible. There are lots of different packet switching devices, but the two most prominent in the modern Internet are **routers** and **link-layer switches**
> 
> Link-layer switches are typically used in access networks, while routers are typically used in the entwork core. The sequence of communication links and packet switches traversed by a packet from the sending host to the receiving host is known as a **route** or a **path** through the network.
#### Transmission Rate
> [!DEFINITION] Transmission Rate
> Transmission rate is a property of a **Communication Link** that measures the bits/second metric of that specific link.
#### ISPs
#ISP
Hosts access the internet through Internet Service Providers (ISPs) including residential ISPs, such as local cable or telephone companies; corporate ISPs; university ISPs; ISPs that provide WiFi access in airports, hotels, coffee shops, and other public places; and cellular ISPs, providing mobile access to smartphones and other devices. These lower-tier ISPs are connected through national and international upper-tier ISPs, and these upper-tier ISPs are connected directly to each other.

> [!INFO] Upper-tier ISPs 
> An upper-tier ISP consists of high-speed routers interconnected with high-speed fiber-optic links.

Each ISP network, whether upper-tier or lower-tier, is managed independently, runs the IP protocol, and conforms to certain naming and address conventions.
#### Protocols
#TCP #IP #HTTP #FTP #PPP #TCP/IP
End systems, packet switches, and other pieces of the Internet run protocols that control the sending and receiving of information within the Internet.

> [!DEFINITION] TCP/IP Stack
>The Transmission Control Protocol (TCP) and the Internet Protocol (IP) are two of the most important protocols in the Internet. The IP protocol specifies the format of the packets that are sent and received among routers and end systems. The Internet’s principal protocols are collectively known as TCP/IP. The usage of these in a system is referred to as the TCP/IP Stack.

Example protols are:
- e.g., TCP, IP, HTTP, FTP, PPP
#### Internet Standards
#RFC #IETF
Given the importance of protocols to the Internet, it’s important that everyone agree on what each and every protocol does, so that people can create systems and products that interoperate. This is where standards come into play.

> [!DEFINITION] Internet Standards
> Internet standards are developed by the **Internet Engineering Task Force** (IETF). The IETF standards documents are called **requests for comments** (RFCs). RFCs started out as general requests for comments (hence the name) to resolve network and protocol design problems that faced the precursor to the Internet. RFCs tend to be quite technical and detailed. They define protocols such as TCP, IP, HTTP (for the Web), and SMTP (for e-mail). There are currently nearly 9000 RFCs. Other bodies also specify standards for network components, most notably for network links. The IEEE 802 LAN Standards Committee, for example, specifies the Ethernet and wireless WiFi standards.

### Service View
#infrastructure #services 
There is another way to view the internet, *as an infrastructure that provides serivces to applications*.
#### Communication Infrastructure
> [!DEFINITION] Communication Infrastructure & Distributed Applications
> The applications are said to be **distributed operations** since they are an amalgamation of services run on multiple hosts. In this sense, the internet is a **communication infrastructure** that facilitates data flow between the hosts that run the distributed bits of the whole application.
#### Socket Interface

> [!DEFINITION] Socket Interface
> End systems attached to the Internet provide a socket interface that specifies how a program running on one end system asks the Internet infrastructure to deliver data to a specific destination program running on another end system. This Internet socket interface is a set of rules that the sending program must follow so that the Internet can deliver the data to the destination program.

Suppose Alice wants to send a letter to Bob using the postal service. Alice, of course, can’t just write the letter (the data) and drop the letter out her window. Instead, the postal service requires that Alice put the letter in an envelope; write Bob’s full name, address, and zip code in the center of the envelope; seal the envelope; put a stamp in the upperright-hand corner of the envelope; and finally, drop the envelope into an official postal service mailbox. Thus, the postal service has its own “postal service interface,” or set of rules, that Alice must follow to have the postal service deliver her letter to Bob. In a similar manner, the Internet has a socket interface that the program sending data must follow to have the Internet deliver the data to the program that will receive the data.
### System View
The internet is "A global network of independently owned and operated networks, all using packet switching technology and the TCP/IP protocol suite."
- Internet: "A network of networks"
	- Loosely hierarchical
	- Public internet vs Private intranet
## Protocols
For human protocols,
- Asking time
- Approaching a stranger to ask something
- Introductions
- ...
Specific messages sent and specific actions taken when these messages are received. For network protocols the analogy is done with the communication done among machines rather than humans and all communication activity in the entirety of Internet being governed by **protocols**.

> [!IMPORTANT] Protocols Define:
> 1. ***Format of messages***, sent & received (among hosts/network entities)
> 2. ***Actions taken*** on message transmission & reception.

## Network Edge
### End Systems (Hosts)
- Run application programs
- e.g. Web, email
- at "edge of network"
- Client/Server Model
	- Client host requests, receives service from always-on server.
	- e.g. Web browser/server, email client/server.
- Peer-peer Model
- Minimal (or no) used of dedicated servers.
- e.g. Skype, BitTorrent

> [!DEFINITION] Cloud 
> Nowadays many servers are located in data-centers, i.e., "cloud" which is a collection of internet services distributed across data centers globally.
### Access Networks & Physical Media
How to connect hosts to edge router?
- Residential access nets
- Institutional access networks (school, company)
- Mobile access networks
Keep in mind:
- Bandwiths of access network
- Shared or dedicated?
#### Residential Access: Point to Point Access
##### Digital Subscriber Line (DSL)
- Uses existing telephone infrastructure
- Up to 2.5Mbps upstream (today basically < 1 Mbps)
- Upto 24Mbps downstream (today basically < 10 Mbps)
- Dedicated phyiscal line to telephone central office. 