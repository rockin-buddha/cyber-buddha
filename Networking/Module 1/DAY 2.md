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
	
### MTU AND FRAME SIZE
---
- **MAXIMUM TRANSMIT UNIT (MTU)** : Maximum Payload size
- **JUMBO FRAMES** : Frames with more than 1500 bytes payload
- Jumbo frames are not standard though supported by some vendors
- 14 byte header + 4 byte trailer results in Overall Ethernet Frame Size Range of 64-1518 bytes
- **COLLISION FRAGMENT or RUNT** : Any Frame less than 64 bytes length
- Collision Fragment or Runt is automatically discarded by the receiving nodes

## ETHERNET SWITCHES
---
- **ETHERNET SWITCH** : Hardware device with multiple ports that connects multiple Ethernet nodes
- Switch Size, Type, Number and Speed of Ports depend on the Switch Vendor and Specific Model
### FORWARDING DECISIONS
---
- Ethernet nodes may have one or more Ethernet switches connecting between them
- When a node generates an Ethernet frame and sends it on the wire, the frame is received by the switch
- Switch need to learn where the Destination Node resides (which of the ports the frame should be sent)

#### MAC ADDRESS TABLE
---
- An Ethernet Switch forwards the frame based on the Destination MAC Address
- **MAC ADDRESS TABLE** : A switch builds and maintains forwarding database with MAC Addresses
- MAC Address Table contains Destination MAC Address to exit port mappings
- Entries are populated based in the source MAC of incoming Frames
- Entries  learned dynamically have an aging time. If they are not used within a defined time, they are flushed from the table
- Static entries can be configured which are not aged out and will remain in the table until manually removed

#### FORWARDING UNICAST FRAMES
---
- **UNICAST ADDRESS** : Represent a single interface in the network
- **UNKNOWN UNICAST FRAMES** : Frames with no matching entry in MAC Address table
- Unknown Unicast Frames are flooded (Sent on all ports, except the incoming port)
- **KNOWN UNICAST FRAMES** : Frames for which their destination MAC Address have a matching entry in MAC Address Table
- Known Unicast Frames are forwarded to the specific ports

#### FORWARDING BROADCAST FRAMES
---
- **BROADCAST ADDRESS** represents all the nodes in a Network as the Destination
- Broadcast Frames are identified by a Special MAC Address where all bits are set to one (Hex Representation : FF:FF:FF:FF:FF:FF)
- When Switch receives Broadcast Frames, it floods them

#### FORWARDING MULTICAST FRAMES
---
- **MULTICAST ADDRESS** represents a selected group of nodes in the network
- Multicast Frames  are identified by special MAC Addresses where Least Significant Bit of the First Octet is set to 1 (Hex Representation : 01:XX:XX:XX:XX:XX)
- Ethernet Switches don't have logic to forward Multicast Frames to group members. Hence they are flooded.

### LAYER 3 SWITCHES
---
- Traditional Switches operate at Layer 2 of OSI Model where packets are sent on a specific Switch port based on Destination MAC Addresses
- Routing operates at layer 3 where packets are forwarded based on Destination IP Addresses, often referred to as a Multi-Layer Switch
- Layer 3 Switch combines the functionality of Switch and Router adding flexibility to a Network
