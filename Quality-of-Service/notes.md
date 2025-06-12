RFC 4594 recommends the DF marking for best effort traffic.
RFC 4594 recommends the AF2x (AF21, AF22, AF23)  marking for high priority data traffic.
RFC 4594 recommends the AF4x (AF41, AF42, AF43) marking for interactive video traffic.
RFC 4594 recommends the AF3x (AF31, AF32, AF33) marking for streaming video traffic.
RFC 4594 recommends the EF marking for voice traffic.
The IPP precedence field was 3 bits in length.

DF = DSCP 0
EF = DSCP 46
AF11 = DSCP 10
AF12 = DSCP 12
AF13 = DSCP 14
AF21 = DSCP 18
AF22 = DSCP 20
AF23 = DSCP 22
AF31 = DSCP 26
AF32 = DSCP 28
AF33 = DSCP 30
AF41 = DSCP 34
AF42 = DSCP 36
AF43 = DSCP 38

CoS/PCP 0 = Best Effort
CoS/PCP 3 = critical applications
CoS/PCP 4 = video traffic
CoS/PCP 5 = voice traffic

CS0 = DSCP 0
CS1 = DSCP 8
CS2 = DSCP 16
CS3 = DSCP 24
CS4 = DSCP 32
CS5 = DSCP 40
CS6 = DSCP 48
CS7 = DSCP 56

Shaping buffers traffic in a queue if the traffic rate goes over the configured rate.
Best Effort delivery means there is no guarantee that data is delivered or that it meets any QoS standard.
Policing drops traffic in a queue if the traffic rate goes over the configured rate.

Cisco ILP offers 7 watts of power.
Cisco ILP uses 2 powered wire pairs.
Electronic devices use DC power
Tail drop is harmful because it can lead to TCP global synchronization
When packets are dropped due to a full queue, it is called tail drop
If an IP phone is connected to a switchport, the QoS trust boundary should be at the IP phone
IP phones mark their call signaling traffic as PCP/CoS 3
LLQ designates one or more queues as strict priority queues.

PoE: power policing can be configured to prevent a PD from taking too much power.

PoE (Type 1) offers 15 watts of power
PoE (Type 1) uses 2 powered wire pairs

PoE+ (Type 2) offers 30 watts of power
PoE+ (Type 2) uses 2 powered wire pairs

PoE (Type 1) is IEEE 802.3af
PoE+ (Type 2) is IEEE 802.3at

UPoE (Type 3) is IEEE 802.3bt
UPoE (Type 3) offers 60 watts of power
UPoE (Type 3) uses 4 powered wire pairs

UPoE+ (Type 4) is IEEE 802.3bt
UPoE+ (Type 4) offers 100 watts of power
UPoE+ (Type 4) uses 4 powered wire pairs

Q: PoE: What does PD stand for?
Powered Device
Q: PoE: What does PSE stand for?
Power Sourcing Equipment
Q: What does Cisco ILP stand for?
Cisco Inline Power
Q: What does FIFO stand for?
First In First Out
Q: What does PoE stand for?
Power over Ethernet
Q: What does POTS stand for?
Plain Old Telephone Service

Q: What does PSTN stand for?
Public Switched Telephone Network
Q: What does VoIP stand for?
Voice over IP
Q: What is considered acceptable jitter for interactive audio traffic?
30 ms or less
Q: What is considered acceptable loss for interactive audio traffic?
1% or less
Q: What is considered acceptable one-way delay for interactive audio traffic?
150 ms or less
Q: When the switchport voice vlan command is applied to an interface, which traffic will be tagged?  Traffic from the PC or from the IP phone?
Traffic from the IP phone
(traffic from the PC will be untagged as usual for an access port)

QoS: Delay (=one-way delay) is the amount of time it takes traffic to go from source to destination.
(Two-way delay measures both ways)
QoS: Loss is the percentage of packets that do not reach their destination.
QoS: Jitter is the variation in one-way delay between packets sent by the same application.
QoS: Bandwidth refers to the overall capacity of a link.
QoS: By default, queued messages will be forward in a FIFO manner

Q: What does RED stand for? 
Random Early Detection 
Q: QoS: What does WRED stand for?
Weighted Random Early Detection
Q: QoS: What features drop random packets when traffic queues pass a certain threshold?
RED / WRED
Q: DSCP: What does AF stand for?
assured forwarding
Q: DSCP: What does CS stand for?
class selector
Q: DSCP: What does DF stand for?
default forwarding
Q: DSCP: What does EF stand for?
expedited forwarding
Q: What does CBWFQ stand for?
Class-Based Weighted Fair Queuing
Q: What does IPP stand for?
IP Precedence
Q: What does LLQ stand for?
Low Latency Queuing
Q: What does NBAR stand for?
Network Based Application Recognition
Q: What Layer 2 header field can be used for QoS markings?
PCP / CoS
Q: What Layer 3 header field can be used for QoS markings?
DSCP (formerly IPP)
Q: What QoS scheduling algorithm uses a weighted round-robin scheduler while guaranteeing a minimum bandwidth to each queue?
CBWFQ
