# ETHERNET FUNDAMENTALS
---
## ETHERNET TECHNOLOGY
---
- Ethernet operates in the Data Link Layer and Physical Layer of OSI Model
	- Data Link Layer 
		- Defines the functional and procedural means to transfer Data between Network Nodes
		- Detect errors that can occur in the physical layer
	- Physical Layer
		- Defines Electrical or Optical Properties and the transfer speed of the Physical Connection between Network Nodes
	- Ethernet is predominant in LAN technology
	- Delivers higher levels of performance
	- Maintains backward compatibility
	- Designed to suit the needs of broad range of applications

## ETHERNET ADDRESSING
---
- Ethernet allows nodes that are connected to the same LAN to communicate with one another by sending **ETHERNET FRAMES** to each other
- Ethernet nodes are identified with a unique address known as the **MEDIA ACCESS CONTROL ADDRESS (MAC ADDRESS)**
- Ethernet frame header contains a Source and Destination MAC Address
- The frame is then forwarded based on where the destination node resides (based on destination MAC Address)

## ETHERNET NETWORK ADAPTERS
---
- **NETWORK INTERFACE CARD (NIC)**: Hardware component that connects a node to the network
- NIC allows devices to communicate over a network, either by using cables or wirelessly
- NIC is Physical Layer and Data Link Layer Device
- At the Physical Layer, NIC provides access to Physical Medium
- At the Data Link Level, NIC provides a Low Level Addressing System using MAC Addresses

## MAC ADDRESS
---
- **MEDIA ACCESS CONTROL ADDRESS (MAC ADDRESS)** : Unique identifier assigned to a Network Interface for use as a Network Address and communication within a local network
- Burned on the Network Adapter's Hardware by the Vendor
- **ETHERNET STANDARD**: Every Ethernet Vendor Register with IEEE and assigned with an OUI (Organisationally Unique Identifier)
- 48 bit long represented in 12 Hexadecimal Digits
	- 6 left hex digits represent OUI
	- 6 right hex digits represent the Serial Number assigned by the Vendor

## IDENTIFY MAC ADDRESSES OF NETWORK INTERFACES
---
- LINUX : 

```bash
ifconfig
  (or)
ip addr
```

- WINDOWS : 
```PowerShell
ipconfig /all

Output : 
Physical Address. . . . . . . . . xx-xx-xx-xx-xx-xx
```
- MAC Address is listed as a series of 12 Hexadecimal Digits, each pair is separated by either a `-` or `:` 

## ETHERNET FRAME STRUCTURE
---
- Data Link Layer is responsible for the Data Transfer over the Physical Medium. Hence the Ethernet Frame that can be carried over the Network is created
- Ethernet Frame includes the following fields:
	- **PAYLOAD** : 
		- Protocol Data Unit received from the upper layer
		- Part that is Encapsulated with Layer 2 Header to construct a Frame
		- **Destination MAC Address** : Specifies the node for which Frame is intended
		- **Source MAC Address** : Specifies the node sending the frame
		- **Type/EtherType** : Indicates the Upper Layer Protocol Type such as IPv4 Packet 
		- **Length** : Length field is used in place of EtherType in some Headers
		- **FCS** : Frame Check Sequence is added at the end of the frame used to detect corrupted frames. 
	- When corrupted frames are dropped, Ethernet doesn't retransmit them. 
> [!NOTE]
	- Standard Ethernet Frame : Composed of Payload encapsulated with a layer 2 header and a trailer
	
