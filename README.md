# Hyperledger Fabric - QRadar SIEM
The following is about illustrating the use of channel-based events of Hyperledger Fabric, and to redirect captured event/incidents to a QRadar SIEM. 
## Hyperledger Fabric
Hyperledger Fabric is a blockchain framework implementation and one of the Hyperledger projects hosted by The Linux Foundation. Intended as a foundation for developing applications or solutions with a modular architecture, Hyperledger Fabric allows components, such as consensus and membership services, to be plug-and-play. Hyperledger Fabric leverages container technology to host smart contracts called “chaincode” that comprise the application logic of the system.

Hyperledger Fabric has multiple security mecanisms, and users activities interacting with the Blockchain generates events and incidents. These incidents and events can be captures and send to application in order order to exploit them.

![alt text](https://goupadhyblog.files.wordpress.com/2017/02/blockchain2.png?w=662 "HLF standards Events & Incidents")

### Channel-based event service
Hyperledger Fabric aka HFL introduces channel-based events. These events are similar to the existing events, however are specific to a single channel. The client handling of channel-based events has a few new options when setting up a listener. Channel-based events are a new feature of the Hyperledger Fabric Node.js client as of v1.1.

A client application may use the Fabric Node.js client to register a "listener" to receive blocks as they are added to the channel ledger. We call these "channel-based events", and they allow a client to start to receive blocks from a specific block number, allowing event processing to run normally on blocks that may have been missed. The Fabric Node.js client can also assist client applications by processing the incoming blocks and looking for specific transactions or chaincode events. This allows a client application to be notified of transaction completion or arbitrary chaincode events without having to perform multiple queries or search through the blocks as they are received.

The service allows any user to receive "filtered" block events (which contain no sensitive information, in other words). Receiving "unfiltered" block events requires read access to the channel. The default behavior is to connect to receive filtered block events. To connect to receive unfiltered block events call connect(true) (see below).

Note that if you register for a block event and then submit a transaction, you should not make any assumptions about which block contains your transaction. In particular, you should not assume that your transaction is in the block associated with the first block event received after registration to the peer's channel-based event service. Instead, you may simply register for a transaction event.

### APIs on the Channel
* newChannelEventHub(peer) -- A Channel instance method to get a new instance of a ChannelEventHub.
* getChannelEventHubsForOrg -- Gets a list of ChannelEventHubs based on an organization. If the organization name is omitted then the current organization of the current user is used.

### Starting a full HLF stack

## QRadar SIEM
IBM® Security QRadar® SIEM is a network security management platform that provides situational awareness and compliance support. QRadar SIEM uses a combination of flow-based network knowledge, security event correlation, and asset-based vulnerability assessment.

IBM is bringing free QRadar to a wider audience with Community Edition. Community Edition is a fully-featured version of QRadar that is low memory, low EPS, and includes perpetual license.
QRadar Community Edition can be downloaded here: https://www.ibm.com/account/reg/signup?formid=urx-32552

### Installing QRadar Community Edition
Install IBM Security QRadar Community Edition in a virtual machine. Community Edition is based on QRadar 7.3.0, and is released without a warranty. 
Check your Linux guest version. Please issue the following command:
```
cat /etc/redhat-release
```
Q: What is your OS Release version? __________________________________________________

### Before you begin
You must have a system with a CentOS Linux 7.3 minimal installation that is connected to the internet, and that meets the following requirements to install QRadar Community Edition. Use 8 GB for the SWAP partition and the defaults for other partitions when you install your operating system. Disable SELinux to avoid a system restart during installation.

Check your Linux guest CPU configuration. Please issue the following command:
```
lscpu
```
Q: How much vCPU do you have? __________________________________________________

Check your Linux guest Memory. Please issue the following command:
```
lsmem
```
Q: How much GB of Memory do you have? __________________________________________________

Check your Linux guest disk partitioning. Please issue the following command:
```
lsblk
```
## From Hyperledger Fabric To QRadar SIEM
