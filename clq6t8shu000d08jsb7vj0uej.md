---
title: "OSI Model"
datePublished: Fri Dec 15 2023 15:55:02 GMT+0000 (Coordinated Universal Time)
cuid: clq6t8shu000d08jsb7vj0uej
slug: osi-model
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702655553242/4a6b84db-932d-4f95-9774-9c86cc1194a6.png
tags: javascript, web-development, rust, internet, osi-model, osimodel

---

Have you ever considered how information moves from one computer application in a device to another computer application in another device? This article is about the OSI Model, which I found interesting enough to write about.

**This is a pretty big article but i learned a lot while writing this.**

**Let's understand the OSI Model of the Internet :**

### **The Basics:**

* OSI model was developed by the International Organization for Standardization (ISO) in 1984, and it is now considered an architectural model for inter-computer communications.
    
* OSI stands for Open System interconnection.
    
* OSI model divides the whole task into seven smaller and manageable tasks. Each layer is assigned a particular task.
    

### The Layers:

1. Application Layer
    
2. Presentation Layer
    
3. Session Layer
    
4. Transport Layer
    
5. Network Layer
    
6. Data-Link Layer
    
7. Physical Layer
    

**Let's learn about these layers in detail:**

1. ### <mark>Application Layer</mark>
    

The application layer is used by network applications (browsers, chat applications, email applications, etc.) on your computer to establish an Internet connection. These applications use various protocols such as HTTP or HTTPS to establish a connection. There are a variety of other internet protocols that collectively form the application layer.

For example, file transfer is done with the help of the FTP protocol. Web surfing is done with the help of HTTP or HTTPS. For emails, the SMTP protocol is used, and for virtual terminals, TELNET is used.

So, the application layer provides services for network applications with the help of protocols to perform users' activities.

1. ### <mark>Presentation Layer</mark>
    

It receives data from the Application Layer. The Presentation Layer performs three basic functions:

* **Translation,**
    
* **Compression, and**
    
* **Encryption/Decryption.**
    
* Translation: The data is in the form of characters and numbers, which the Presentation Layer converts into a machine-understandable binary format. For instance, it can convert ASCII to EBCDIC code. This function of the Presentation Layer is known as Translation. Additionally, before transmitting the data, the Presentation Layer reduces the number of bits used to represent the original data.
    
* Data compression, known as bit reduction, can be either lossy or lossless. It reduces the space required to store the original file, enabling faster data transmission. This makes data compression particularly useful for real-time video or audio streaming.
    
* Before data is transmitted, it is encrypted to maintain its integrity and enhance the security of sensitive information. Encryption occurs at the sender's end, while decryption takes place at the receiver's end. The SSL protocol (Secure Sockets Layer) is utilized in the Presentation Layer for encryption and decryption.
    

1. ### <mark>Session Layer</mark>
    
    It manages the following:
    

* Session management,
    
* Authentication, and
    
* Authorization.
    

Session Layer helps in setting up and managing connections enabling sending and receiving of data followed by termination of connections or sessions. The session layer too has helpers called APIs or Application Programming Interfaces. NETBIOS or Network Basic Input/Output System is an example of an API that allows applications on different computers to communicate with each other. Just before a session or a connection is established with a server, the server performs a function called Authentication.

Authentication is the process of verifying, Who you are. For this, the server uses a username and password. Once the entered user name and password are matched, a session or a connection is established between your computer and the server. Now, you can upload or download the required files. After authenticating the user, Authorization is checked.

Authorization is the process used by the server to determine if you have permission to access a file. If not, you will get a message saying, You are not authorized to access this page. Both of these functions, Authentication and Authorization, are performed by the session layer. The session layer keeps track of the files being downloaded.

For example, a web page contains text, images, etc. These text and images are stored as separate files on the web server. When you request a website in your web browser, your web browser opens a separate session to the webserver to download each of these text and image files. These files are received in the form of data packets.

The session layer keeps track of which data packet belongs to which file, either a text file or image file, and tracks where the received data packet goes, in this case, it goes to the web browser, that is, the session layer helps in Session Management.

1. ### <mark>Transport Layer</mark>
    

* segmentation,
    
* flow control,
    
* error control,
    
* Connection and connectionless transmission etc.
    

The transport layer controls the reliability of communications through segmentation, flow control, and error control. In segmentation, data received from the session layer is divided into small data units called segments.

Each segment contains a source and Destination port number and a sequence number. The port number helps to direct smaller data units to the correct application. Sequence number helps to reassemble smaller data units in the correct order to form the correct message in the receiver.

In Flow control, the Transport Layer controls the amount of data transmitted to a level that the receiver can process. Consider our mobile connected to a server. Server can transmit data maximum at 100 Mbps and Mobile can process data maximum at 10 Mbps. Now, we are downloading a file from the server but the server starts sending data at 50 Mbps which is greater than the rate a mobile phone can process. So, a mobile phone, with the help of the Transport Layer, can tell the server to slow down the data transmission rate up to 10 Mbps so that no data gets lost.  
If some data units do not arrive at the destination, the transport layer uses Automatic repeat request (ARQ) schemes to retransmit the lost or corrupted data.

Protocols of the Transport layer are Transmission Control Protocol (TCP) and User Datagram Protocol (UDP). Transport Layer provides two types of services: Connection-oriented Transmission and, Connectionless Transmission. Connection-oriented Transmission is done via TCP while Connectionless Transmission is done via UDP.Eg. Streaming movies, songs, online games, Voice over IP, TFTP, DNS, etc. On the other hand, TCP is used where full data delivery is a must. Eg. World Wide Web, Email, FTP, etc.

1. ### <mark>Network Layer</mark>
    

The transport layer passes data segments to the Network Layer: The network layer works for the transmission of received data segments from one computer to another located in different networks.

The network layer works for the transmission of received data segments from one computer to another located in different networks.

Segments in the Network Layer are called Packets. It is the layer where routers reside.

The functions of the Network layer are:

1. Logical Addressing
    
2. Routing
    
3. Path determination
    

Logical Addressing: IP addressing (IPv4 or IPv6) done in the network layer is called Logical addressing. Every computer in a network has a unique IP address.

As the network layer deals with data delivery, this layer assigns the sender and receiver IP addresses to each data packet so that each data packet can reach the correct destination. Routing Routing is a method of moving a data packet from source to destination and it is based on the logical address format of IPv4 or IPv6.

Suppose, Computer A is connected to network 1 and Computer B is connected to network 2. Network, in simple terms, means multiple laptops or smartphones connected to a Home Router. From computer B, we have requested to access [facebook.com](https://www.youtube.com/watch?v=undefined&t=552s) and now there is a reply from the Facebook server for computer B in the form of a packet.

This packet needs to be delivered to Computer B only. Since, in a network, each device has a unique IP address, so these both computers will have a unique IP address as well. The network layer of the Facebook server has already added the sender and receiver IP address in the packet.

This mask tells that the first 3 combination represents the network while the last combination represents the host or Computer B. So, based on the IP address format, the received data packet will move to network B1 and then to computer B. So, based on IP address and mask, routing decisions are made in a computer network.

Path determination A computer can be connected to any internet server or a computer in several ways. Choosing the best possible path for data delivery from source to destination is called Path Determination. Layer 3 devices use protocols such as OSPF (Open Shortest Path First), BGP (Border Gateway Protocol), and IS-IS (Intermediate System to Intermediate System) to determine the best possible path to deliver data.

1. ### <mark>Data Link Layer</mark>
    

The data link layer receives data packets from the Network Layer which contain the IP addresses of the sender and receiver. There are two kinds of addressing: - Logical addressing and physical addressing Logical addressing is done at the network layer where the sender and receiver's IP addresses are assigned to each data packet. Physical addressing is done at the Data Link layer where MAC addresses of both devices are assigned to the received data packet.

MAC address is a 12-digit alphanumeric number embedded in the NIC of your computer by the manufacturer. The data unit in the Data link layer is called Frame. The Data Link Layer is embedded as software in the NIC of a computer and provides a means to transfer data from one computer to another via local media. Local media includes Copper wire, optical fiber, or Air for radio signals.

Please note, here media does not correspond to audio, video, animation, etc. It refers to the physical links between two or more computers or networks. The Data Link layer performs two basic functions: - It allows the upper layers to access the media using techniques such as framing. - Controls how data is placed and received from the media using techniques such as media access control and error detection.

Access the media: Consider two distant hosts, a laptop and a desktop, communicating with each other. As laptops and desktops are connected to different networks, they will use Network layer protocols, IP for example, to communicate with each other. In this example, the desktop is connected to Router R1 via an Ethernet Cable.

Router R1 and R2 are connected via a satellite link and the laptop is connected to router R2 via a Wireless Link. Now, the desktop wants to send some data to Laptop. Based on the medium used to connect the desktop and Router R1, the Data Link layer - embedded as software in the NIC of the desktop adds some data in the head and tail of the IP packet and converts it to a frame, an Ethernet frame in this case.

Router R1 receives this Ethernet frame, decapsulates it to an IP packet, and then encapsulates it again to a frame so that it can cross the satellite link to reach router R2. Router R2 will again de-capsulate the received frame and re-encapsulate based on the medium used to connect router R2 and laptop, wireless data link frame in this case.

The laptop receives a wireless data link frame, de-capsulates, and then forwards the IP packet to the Network layer and finally to the application layer. Application layer protocols then make received data to be visible on a computer screen. So, network layer or higher level layers can transfer data over media, which are LAN Cable and Air in this case, with the help of Data Link Layer.

That is, the Data Link Layer provides access to media for higher layers of the OSI Model. The data link layer controls How data is placed and received from the media. Data Link Layer sends and receives frames from the media. The technique used to get the frame on and off the media is called Media Access Control. There may be several devices connected to a common media.

If two or more devices send data at the same time, then there may be a possibility of the collision of the two messages resulting in a useless message that neither recipient can understand. To avoid these situations, the data link layer keeps an eye on when the shared media is free so that the device can transmit data to the receiver.

This is called Carrier Sense Multiple Access CSMA. So, the Data Link Layer, with its Media Access Control methods, controls when data is placed and received from the media. The tail of each frame contains Bits that are used to detect errors in the received frame. These occur due to certain limitations of media used for transferring data.

1. ### <mark>Physical Layer</mark>
    

Till now, data from the application layer has been segmented by the Transport Layer, placed into packets by the Network Layer, and framed by the Data Link Layer which is a sequence of binary 0s and 1s. The physical layer converts this binary sequence into signals and transmits them over local media. It can be an electrical signal in the case of a Copper Cable or LAN cable, a Light signal in the case of Optical Fibre, and a Radio signal in the case of Air as Local Media.

So, the signal generated by the Physical Layer depends on the type of Media used to connect the two devices. At the receiver side, the Physical layer receives signals, converts them into bits, and passes them to the Data Link Layer as a frame and then to higher layers, finally to the application layer. Application layer protocols make the sender's message visible in the application on the receiver's computer screen.

So, these are 7 layers of the OSI Model lying behind the smooth functioning of the Internet.