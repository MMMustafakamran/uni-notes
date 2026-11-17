# Computer Networks Notes (transcription)

Auto-transcribed from `Cnet.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
```text
```

## Page 2
### Transport Layer
#### Transport vs Network layer service
#### Transport layer Actions
```text
Transport Layer #10
Provides logical communication b/w app processes on diff host
break message -> segments
Transport vs Network layer service
logical comm
logical comm
b/w processes
Transport layer Actions
* Reciever
recieves segment from IP
check header value
extract application layer message
demultiplex message up to application via socket
* sender
finds header value
creates segment
gets app application layer message
TCP
UDP
transmission control Protocol
reliable
congestion control
flow control
connection setup
```

## Page 3
#### Multiplexing / Demultiplexing
#### TCP Header Datagram
```text
Multiplexing / demulti..
L technique to allow multiple data streams to share communication
channel - uses source port no
Explanation
TCP
1. Data constantly from application layer
converts Bytes to segments
segments
11101010
Bytestream
Connection oriented
2. uses 3 way handshake
2
3
Full Duplex
4
Piggybacking
3.
B
error control
5
4. can send data with acknowledgement
6
flow control
congestion control
Using GBN or SR
7
5.
to make sure buffer capacity of reciever not
exceeded
TCP Header Datagram:
Source Port 16 bit
Destination Port 16 bit
Seq No 32
bit
every byte has seq
Acknowledge
No 32 bit
Checksum 16bit
URGENT POINTER 16
```

## Page 4
#### UDP demultiplexing
```text
Multiplexing
L combines data from multiple application /sockets into single stream for transmission
At recieving Host Demultiplexing
Directs data to correct application
when Datagram arrives, Transport layer examines ports
to deliver to
* UDP demultiplexing
L Dst port influences destination only
Application
P3
APP
()
transport
transport
trans
network
link
server socket
physical
Datagram mysocket2 =
new DatagramSocket
new DatagramSocket(9157);
(6428);
new DatagramSocket(5773);
src port = 6428
dst port = 9157
so
socket identified
by
dst port no
srcport = 9157
dst port = 6428
TCP
socket identified by
src port no.
dst IP address
src IP address
if two client send data to same dst IP, but they would have diff src IP, ports so
easily differentiated
```

## Page 5
```text
Multiplexing / demulti..
L technique to allow multiple data streams to share communication
channel - uses source port No
Explanation
TCP
1. Data constantly from application layer
Bytestream
11101010
2. uses 3 way handshake
Connection oriented
Full Duplex
3
4
Piggybacking
3.
A
B
error control
5
4. can send data with acknowledgement
6
flow control
congestion control
Using GBN or SR
7
5.
to make sure buffer capacity of reciever not
exceeded
TCP Header Datagram:
Source Port 16 bit
Seq No 32
bit
every byte
has seq
Acknowledge
No 32 bit
HLEN
4bit
Checksum 16bit
URGENT POINTER 16
```

## Page 6
```text
Multiplexing
L combines data from multiple application /sockets into single stream for transmission
At recieving Host Demultiplexing
Directs data to correct application
when Datagram arrives, Transport layer examines ports
UDP demultiplexing
to deliver to
L Dst port influences destination only
Application
P3
APP
APP
transport
transport
trans
network
link
physical
server socket
Datagram mysocket2 =
new DatagramSocket
new DatagramSocket(9157);
(6428);
new DatagramSocket(5773);
so
socket identified
by
dst port no
srcport = 9157
dst port = 6428
TCP
socket identified by
src port no.
dst IP address
src IP address
if two client send data to same dst IP, but they would have diff src IP, ports so
easily differentiated
```

## Page 7
#### UDP
#### UDP segment format
#### Internet Checksum
```text
UDP
simple = only multi/demulti, framing, No connection related
Besteffort = No error correction, No guarantee
connectionless = No handshake.
Advantages
No connection Delay
Streaming
DNS (Domain Name system) : DNS small quick queries can be resent if lost
SNMP (simple network management protocol) SNMP uses UDP if network congested
32 bits
src port # dst port #
length
checksum
Length of
App data
bytes of
(payload)
UDP segment format
Internet Checksum
L detects errors
1. sender computes checksum by summing content of segment in 16 bit integers
then take
1s compliment
2. verification at Reciever if checksum same
However some cases incorrect as wraparound (carry)
so not 100% correct
```

## Page 8
#### RDT 2.0
```text
RDT 1.0 was basic didnt have
error control
RDT 2.0
checksums
ACKs
Negative Acknowledgement (NAKs): inform sender Data incorrect
Stop and wait: sender sends 1 packet and waits for Ack or NACK
before sending next packet
Flaw in RDT 2.0
L corrupted Ack/NAKs
so
sender retransmits current pkt
sender adds sequence No to each
reciever discards duplicate (if received)
Sender Protocol
rdt_send(data)
sndpkt
retransmit
waiting for
wait for
ACK or
call 0 from
above
NAK 0
rdt_rcv(rcvpkt)
sender
&& notcorrupt(rcvpkt)
includes
sequence
no #0
wait for
call 1 from
above
```

## Page 9
#### Performance of rdt 3.0
#### Pipelined protocol
```text
Performance of rdt 3.0 (stop and wait)
Usender = Utilization time sender busy sending
example : 1 Gbps link, 15ms prop delay, 8000bit packet
8000 = 8x10^-6 s
Dtrans =
1x10^9
rdt3.0:
sender
receiver
t=0
first packet arrives
last pkt arrives, send Ack
RTT
ACK
received
L/R
t=RTT+L/R
Usender =
0.00027
RTT+L/R
spent actually
so performance
sending
bad
pipelined protocol
L sender allows multiple 'In flight', yet to be Acked packets
range of seq No must be increased
Sender keeps
instead of stop/wait
sending packets
0
t=0
R
RTT
Utilization more
ACK
ACK
ACK
```

## Page 10
#### Go-Back-N
```text
Go-Back-N: sender
total packet that can be in flight
To track all packet in window
K-bit seq No in pkt header
cummulative ACK, ACK(N)
Acks all packs up #seq
on recieving ACK(N)
move window = window + N+1
Timer for oldest inflight packet
reciever
L ACK sent by highest seq no recieved in order
out of order packet
discarded
buffer
pkt 0
ACK 0
2
ACK1
discard 3, resend ACK1
(wait)
4
discard 4, resend
ACK1
5
discard 5
resend
ACK1
ACK1 duplicate
ignored
pkt 2 timeout
2
```

## Page 11
#### Select Repeat
```text
Select Repeat
L reciever individually Ack all packet
Buffer packets for inorder delivery to upper layer
L sender times out/ retrans individually for all un Acked pkts.
window :
Acked
pkt 0
ACK0
ACK1
3
buffer, ACK3
(wait)
4
5
buffer, ACK4
buffer, ACK5
(resend ACK)
2 timeout
2
rcv pk2, deliver pk2,3,4,5, send ack2
* seq # size should be double to window size
```

## Page 12
#### TCP datagram
#### Timeout value
```text
TCP datagram
src port # dst port #
sequence No
ACK No
C,E
checksum
options
RSF
App data
Host A
Host B
Seq=42, ACK=79
data=c
seq=79, ACK=43, data=c
seq=43, ACK=80
Timeout value?
L Depending on RTT
set
To figure out
SampleRTT
L time from transmission to Ack recieved
Avg several
EstimatedRTT = (1-a) * EstimatedRTT + a * SampleRTT
a = typically = 0.125
typical
Timeout interval = estimatedRTT + 4* DevRTT
B = 0.25
so
safety margin
DevRTT = (1-B)*DevRTT + B*| SampleRTT - EstimatedRTT |
```

## Page 13
### Congestion control
#### Causes of congestion
```text
o Arrival of inorder segment
L Reciever may delay Ack upto 500 milliseconds to
additional order seg may arrive
o Fast transmit
Host A
x
ACK100
ACK100
ACK100
3 time so 1 sent
Congestion control
diff from flow control as flow is speed matching
of 1 sender, 1 reciever
while congestion control about multiple sender
cause: sender send more than reciever
impact
Packet loss
Causes
1. Ideal => infinite buffers capacity
No packet loss, throughput = sending rate
throughput
but if sending rate > throughput
queuing happens in buffers
Host
infinite buffer
```

## Page 14
#### Congestion cost
```text
2. Finite buffer
2a. Retransmission due to overflow
lin > lout so queuing => overflow -> retransmission
read reduces
throughput lout
L retransmission further decreases lout
lin < l'in
doesn't increase
successful prior
of packet that are succesfully sent without needing retransmission
effective
arrival rate
R/2
capacity
due to
3. Multi Hop Network
lout
lin
Host
Router1
Router2
if packet goes through 1st Router, but lost at 2nd it need retransmission again
R/2
lout
retransmission overwhelm, chain
so lout goes to zero
lin
Congestion Cost
High Delay
Throughput: can't increase throughput more than capacity (R/2)
wasted
retransmission
multihop
```

## Page 15
#### Approaches to Congestion Control
#### Ways of Congestion Control: AIMD, Slowstart
```text
Approaches to Congestion Control
End-End Congestion control
1-
Detect congestion if
packet lost when no Ack = timeout
measure RTT, if high = congestion
Network
doesnt give any feedback
Sender only involved, reciever
original TCP worked on this
Network Assisted
L Feedback : ECN
explicit congestion notification
Actively adjust
L Dont wait for Acks or timeout to determine
3 dup = half
Ways of Congestion Control
Reno
Classical
1. Additive Increase, multiplicative Decrease (AIMD)
inc: TCP increases rate (+1) per RTT until Loss
dec: upon Detecting loss, 3 consecutive duplicate Acks (1/2) half rate
L cut to 1MSS size
Sawtooth pattern
lin
by timeout (TcpTahoe)
time
2. Slowstart
(2x)
expon rampup: start slow, double rate n after every RTT upto Network capacity
Transition: switch to (AIMD) when congestion window reaches threshold (ssthresh)
```

## Page 16
#### TCP cubic
#### Advanced Approach: Delay Based
```text
way to 'probe' AIMD for usable bandwidth
TCP cubic
3)
Ramp up towards last loss rate, then cautiously approach
Achieves higher tput than AIMD, optimizing bandwidth use
cwnd
bytes/sec
windowsize = cwnd
TCP rate =
RTT
2.
Same
Advanced Approach
Delay Based
L use RTT measurement to adjust
congestion
measured
# bytes sent in last RTT
throughput
RTTmeasured
RTTminimum = uncongested path
max throughput without congestion =
cwnd
RTTmin
if throughput way higher mean congestion
Adv
doesnt cause loss to detect congestion
edges it, doesn't overflow
```

## Page 17
```text
Approaches to Congestion Control
1-
End-End Congestion control
Detect congestion if
packet lost when no Ack = timeout
measure RTT, if high = congestion
Network
Sender only involved, Network reciever doesnt give any feedback
original TCP worked on this
Network Assisted
L Feedback : ECN
explicit congestion notification
Actively adjust
L Dont wait for Acks or timeout to determine
Ways of Congestion Control
Timeout = 1
Reno
Classical
1. Additive Increase, multiplicative Decrease (AIMD)
inc: TCP increases rate (+1) per RTT until Loss
dec: upon Detecting loss, 3 consecutive duplicate Acks (1/2) half rate
Sawtooth pattern
by timeout (TcpTahoe)
time
2. Slowstart
expon rampup: start slow, double rate n after every RTT upto Network capacity
(2x)
Transition: switch to (AIMD) when congestion window reaches threshold (ssthresh)
```

## Page 18
```text
AIMD
3)
TCP cubic
Ramp up towards last loss rate, then cautiously approach
Achieves higher tput than AIMD, optimizing bandwidth use
TCP rate =
cwnd
bytes/sec
RTT
2.
Same
Advanced Approach
Delay Based
L use RTT measurement to adjust
congestion
measured
# bytes sent in last RTT
throughput
RTTmeasured
RTTminimum = uncongested path
max throughput without congestion =
cwnd
mean congestion
RTTmin
if throughput way higher
doesnt cause loss to detect congestion
Adv
edges it, doesn't overflow
```

## Page 19
#### Explicit Congestion Notification
#### TCP fairness
#### QUIC
```text
Explicit Congestion Notification
L Network assisted
marked by router
Two bits in IP header
indicate congestion
Destination sets ECE, bit on ACK,
L notifies sender of congestion
TCP fairness
L aim equal sharing of available bandwidth
AIMD
L fair
* Fairness challenge in UDP
L lacks congestion control in UDP
multiple TCP connections enhance throughput
Evolution
TCP lacks built in realtime services, security etc
emergence of HTTP/3 and QUIC
integrate transport
QUIC (Quick UDP Internet Connection)
L App layer protocol running over UDP
reliability
mirrors TCP but
cong control
Faster connection &
but on QUIC = 1RTT
Multistreams
```

## Page 20
### Network layer
#### Routers
```text
Network layer
Control Plane
view
network-wide logic
how datagram routed among
how forwarding of datagram
arriving at router to output port
routers src to dst
Traditional
routing
from transport layer
software
Network layer
defined Network
sender encapsulates segments to datagrams
remote
passes to Link layer
controller
install forwarding
table in router
Routers
examines header in an IP datagram
moves data from input to output port
Functions
forwarding: move packet input to output port
interaction of routing algorithm in control plane
routing: determine route from src to dst
algorithm
Dataplane
forwarding table
```

## Page 21
### Router structure
#### Input port function
```text
* Internet
as simple
L Best effort
L sufficient bandwidth
Router structure
routing processor
control plane
high speed
switching
fabric
Data plane
router input port
output port
* Input port function
link
forwarding,
termination
line
layer protocol
queueing
fabric
decentralized switching
physical
link layer
(receives)
layer
(ethernet)
destination
based on header values
generalized forwarding
based L Dst IP
```

## Page 22
#### Longest Prefix matching
#### Switching fabric
```text
Forw. table
L Ranges of dst IP
go to diff
Link Interface
instead of Range use
Longest Prefix matching
L use longest address prefix that matches dst address for forwarding
e.g
11001000
00010111
00010000
match this with table
choose longest match
second
longest
o usually performed using (TCAMs) ternary content addressable memory
retrieves address in One clock cycle
Switching fabric
L transfer packet input → output link
L switching rate
rate at which packets transferred
R
rate = NR
N input
ports
* 3 types
memory
Bus
interconnected
Network
```

## Page 23
#### Memory
#### Bus
#### Interconnected Network
#### Cisco Router
```text
* 1 Memory
1st Generation
L CPU controls switching
L packet copied to memory
L speed limited by memory bandwidth
* Bus
L speed ≈ bus bandwidth
L speed of bus cable : 32 Gbps
* Interconnected Network
crossbar / other nets initially connect processors in multiprocessor
2x2
crossbar
o multistage switch
L nxn built
from smaller switch
o exploits parallelism
L fragment datagram into cells
(combine after pass)
* Cisco Router
L 8 switching plane
L 3 stage interconnection
8 switch
3 stage
```

## Page 24
#### Input Port queing
#### Head of Line Blocking
#### Output Port Queing
```text
* Input Port queing
if switch fabric slower than input ports combined = queing
delay loss
Head of Line Blocking
L front queued packet may prevents others from
moving forward
- but only upper one goes so blue blocked
- both red want to go
Output Port Queing — occurs at output port if multiple packet need same
outgoing link
datagram
buffer
queing
o which datagram to Drop if no free buffer?
Priority Scheduling
link capacity
Buffering =
RTT · C
√N
```

## Page 25
```text
Q1)
Sample RTT = 106ms, 120, 140, Find ERTT after each sample α = 0.125
and ERTT = 100ms before each . Find Dev RTT
E = (1 - 0.25) × 100 + 0.125 × 106 = 107.0
Dev
= (1 - 0.25) × 5
Timeout
L Estimated
```

## Page 26
### IPv4 Datagram structure
```text
it's a core protocol
IPV4 Datagram structure
32 bits
type of service
ver
head
length
ver : tell IP version, e.g 4 means IPv4
len
16 bit identifier
flags
Header len : length of header, Determining
time to
header
start of payload (actual Data) as it comes
live
checksum
source IP (32bit)
after header, typically 20 bytes
destin IP (32bit)
Type of service: Bits to distinguish type of
options
IP datagrams based on required level of
payload data (variable
length total: header len + payload
max = 65,535 bytes
fragmentation offset
flags, Identifier: Identifies fragments of datagram so can be disassembled
Time to live: ensure datagram doesn't circulate indefinitely
Upper layer protocol: specifies transport layer proto. e.g TCP/UDP
Header checksum: Detecting of bit errors using 1's compliment
Source/Dest IP: Source inserts its IP, Destination found by DNS
Options:
Data (payload)
Overhead:
20 bytes of TCP
20 bytes of IP
= 40 bytes of + app layer overhead
```

## Page 27
### IPv4 Addressing
#### Subnet
#### CIDR
```text
8 bit
8 bits
8
8
IPv4 Addressing.
Structure
L 32 bit no divided into 4 octets
e.g
192.168.1.1
L identifies each host and Interface
Interface: connection b/w host/router and physical link
• router have multiple interfaces eg (each port (different IP))
• hosts have 1 or two interfaces ( wireless or Ethernet.
• Interfaces are connected via Link layer (study later CH#6)
Subnet:
physically
def: devices interfaces that can reach each other with going through
a Router
subnet
e.g
Router
IP address
switch
subnet bits
host bits
223.1.1.3
223.1.1.2
223.1.1.1
subnet = 223.1.3.0/24
first 24
bits are
CIDR
Subnet mask bits
L The (/24) notation is called classless inter Domain Routing
a.b.c.d/x
```

## Page 28
### Host Addressing
#### DHCP
```text
Host Addressing
1. Manually by admin
2. DHCP ( Dynamic Host Config Proto)
L host get IP from server
Advantages
can renew
its lease on address
allow reuse (only hold address if connected)
mobile users can join
• Host broadcast DHCP discover msg
optional
• DHCP server responds with DHCP offer
Host req
IP
: DHCP requesting msg
• DHCP server send address : DHCP ack msg
DHCP server 223.1.2.5
client
discover
DHCP DISCOVER
- client doesn't have IP yet
src: 0.0.0.0,68
used to
dest: 255.255.255.255,67
No dest address just 255.. so to all interface
req and confirm
IP given to host
transaction ID: 654
yiaddr: 0.0.0.0
L UDP dst Port No
offer
- matches offer.
src: 223.1.2.5,67
dst: 255.255.255.255,68
yiaddr: 223.1.2.4
trans: 654
lifetime: 3600sec
request
src: 0.0.0.0,68
dst: 255.255.255.255,67
IP address proposing to use
yiaddr: 223.1.2.4
trans: 655
lifetime: 3600sec
ACK
confirmed
src: 223.1.2.5,67
to use this
dst: 255.255.255.255,68
yiaddr: 223.1.2.4
Host
lifetime: 3600sec
trans: 655
```

## Page 29
```text
DHCP also needs
address of first hop router
name, IP of DNS server
network mask (indicates host portion of address)
prefix
* Longer, more specific subnet is prioritized
e.g
NAT
200.23.16.0/23
send me anything beginning with
200.23.16.0/20
A
200.23.20.0/23
Internet
200.23.30.0/23
send me...
200.23.18.0/23
200.23.18.0/23
• This ip can be part of 200.23.16.0/20 also tho
• Network with Internet will send packets to B network as 23 vs 20
How do ISP get block of addresses?
more specific
Q
prefix
ICANN (Internet corporation for Assigned Names and numbers)
Names
decision on forwarding
table
L stores IP address through 5 regional registries
32 bit address not enough. so use NAT
```

## Page 30
### NAT
### IPv6
```text
NAT
for all outgoing
• replace all priv IP to public
port no
public
port
• store priv IP in translation table
port NO
10.1.2.1, 41
13.12.19.1, 84
10.1.2.2
• replace Dest IP of all incoming data going through translation table
LAN
private
side add
WAN side Add
NAT translation table →
LAN side
13.12.19, 84
10.1.2.1, 41
* Controversy
L routers should only process up to layer 3
L address shortage resolved by IPv6
L violates end-to-end argument (port # manipulation)
IPv6
addresses 32 bit IPv4 shortage of IP
Adv. speed processing 2 = 40 byte fixed length header
• enable diff network layer treatment of flows
```

## Page 31
#### Transition to IPv6 (Tunneling)
```text
What's missing
No checksum
No fragmentation
No options
Tunneling
Transition to IPv6
L Router - IPv6 , IPv4 , IPv6 and v4 hybrid
L Tunneling
if Next Router is IPv4 → convert v6 → v4
if Next IPv6, convert back to IPv6
v6 still intact
v4
encapsulated v6
```

## Page 32
### Generalized Forwarding : SDN
```text
generalized
Forwarding : SDN
New type of forwarding   L old forwarding L we just matched the Dest IP and forwarded it
In this we can match much more than just Dest IP
and then we can Forward / Drop / Modify / Encapsulate
* What we can Match
Src MAC
Dst MAC
Eth
VLAN
VLAN
IP Source
IP Dest
IP
TCP/UDP
Ingress port
Type
ID
Pri
ToS
Src Port Dst Port
Link layer
Network layer
Action
Forward packet to port(s)
Drop Packet (Firewall)
Modify fields in header ( NAT)
Encapsulate, forward to controller
e.g
IP dest = 51.6.0.8 Action: port 6
match
forward to
TCP = 22
Action : drop   Block all datagram going to port 22 TCP
port
Table:
match
Action
in each
Router
IP source = 10.3.*.*
Forward(3)
IP dst = 10.2.*.*
port
in router
```

## Page 33
### Middlebox
```text
Middlebox
L intermediary box performing functions apart from router
```

## Page 34
### CH#6 Link layer
#### 6.1 Introduction
#### Services
```text
CH#6 Link layer
6.1 Introduction
connection of LAN with devices
lowest layer protocol
Includes
L reliable data transfer
L flow control
multiple access problems
LANs ( Local area network)
addressing
framing
Key protocols:
L Ethernet, ARP (Address Resolution Protocol),
also protocol MPLS ( multi-protocol Label switch)
Goals
Error detection
Multiple access problem (How multiple nodes share communication
channel)
Addressing
Nodes: Hosts and routers
Frame : PDU (protocol Data unit) encapsulates IP datagram by
adding header, trailer
MAC address in frame identify src, dst (different from IP)
Services
* Flow control: pacing b/w adj nodes
* error detection : caused by noise, signal attenuation
receiver detects error, signal retransmission, or drop frames
* error correction : receiver finds & corrects bit errors without retransmission
* half duplex, full dup : with half: nodes at both ends of link can transmit but
not at the same time
```

## Page 35
#### Where link layer implemented?
### Error Detection
```text
Where link layer implemented? : In each host
NIC (network interface card)
adapter
• attaches into host's system buses
implemented protocols
• combination of hardware, software, firmware
app
software
transport
network
Link
CPU
memory
datagram
datagram
host bus
Frame
hardware
controller
link H datagram
physical
network
interface
Sending
Receiving
L encapsulates datagram in frame
• find error, flow control, reliable dat...
L add error checking bits, reliable
• extract datagram, passes to upper layer
data transfer, flow control
Error Detection
* Transmission of Data frame
No
bit comp
①
datagram
d data bits
EDC
D
EDC'
Yes
② Transmission
• on sender side, Datagram gets as added with header field and EDC (error detected and correcting bits)
```

## Page 36
#### Parity checking
```text
How EDC computed?
* Parity checking
• detects single bit error by making no total bits even
→ single bit Parity
e.g
0 1 1 1 0 1 0 1 | 1
1
#5 bits(1)
so 6 bits are 1
even
• At receiver
L Check if even or odd
No error
confirm
even
error
No of errors
→ Two Dimensional Parity  • even parity on each row and column
e.g
correct
• can detect error and its location
1 0 1 0 1 | 1
1 1 1 1 0 | 0
0 1 1 1 0 | 1
1 0 1 0 1
if error
should be 1 as 3 (odd)
1 0 1 0 1 | 1
1 0 1 1 0 | 0 × - Parity error
0 1 1 1 0 | 1
1 0 1 0 1
parity error
```

## Page 37
```text
Where link layer implemented? : In each host
NIC (network interface card)
adapter
• attaches into host's system buses
implemented protocols
• combination of hardware, software, firmware
app
software
transport
network
Link
CPU
memory
datagram
datagram
host bus
Frame
Link H Datagram
hardware
controller
link H datagram
physical
network
interface
Sending
Receiving
L encapsulates datagram in frame
• find error, flow control, reliable dat...
L add error checking bits, reliable
• extract datagram, passes to upper layer
data transfer, flow control
Error Detection
* Transmission of Data frame
No
bit comp
①
datagram
d data bits
EDC
EDC'
Yes
② Transmission
• on sender side, Datagram gets as added with header field and EDC (error detected and correcting bits)
```

## Page 38
```text
How
EDC computed?
* Parity checking
→ single bit Parity
• detects single bit error by making no total bits even
e.g
0 1 1 1 0 1 0 1 | 1
#5 bits(1)
so 6 bits are 1
even
• At receiver   L Check if even or odd
No error
confirm
error
even
→ Two Dimensional Parity  • even parity on each row and column
e.g
correct
1 0 1 0 1
1
1 1 1 1 0
0
0 1 1 1 0
1
1 0 1 0 1
if error
1 0 1 0 1 | 1
should be 1 as 3 (odd)
0 × - Parity error
1 0 1 0 1
parity
error
```

## Page 39
#### Internet checksum
#### Cyclic Redundancy Check (CRC)
```text
+ Internet checksum
Sender: sum up D bits and 1's complement it (flip), send actual Data + flipped
checksum
Receiver: flip actual data and compare with checksum received
if match
if not
L correct
L error
* Cyclic Redundancy Check (CRC)
D : data bits (we want to send)
G: bit pattern (generator) of r+1 bits (Given by CRC standard)
sender,
d data bits
r CRC bits
receiver
so
use same
R
D
G
Total bit to send = D+R bits
Can be calculated by = <D,R> = D*2^r
XOR R
left shift Data bits
Sender
L calculate R such that <D,R> exactly divisible by G
No remainder
so
<D,R>
(Y%2=0)
= Any % 2 = 0
G
if remain
Receiver
L Divides <D,R>
L if remainder = error
```

## Page 40
### Multiple Access link
```text
So summing up
Sender :
D·2^r XOR R = nG
add R
divisible by G
left shift
D·2^r
rearrange for
R = remainder
G
ex,
1001
101110
D
so 101110.000
• left shift D r times
r=3
• Divide by G =>
1001 ) 101110000
1001
remainder = 011 = (3) = R
Multiple Access link
L Broadcasting
Communication if multiple sender/receiver on
single communication
point to point
same link = result in collision
L Ways to Broadcast (MAC protocol)
1° channel Partition ( time allocated
to each node)
2° Random Access ( speaking / stopping
if someone speaks)
3° Taking Turns ( hand raising)
polling
token passing
For
centralized
pass the pillow
controller
student
ask each
whoever
member
has it can talk, if
* MAC Address
don't wanna talk pass pillow
L only send req to same subnet
L ARP
```

## Page 41
### ARP
#### Scenario 1
#### Scenario 2: Host A to Host C
```text
Arp
48bit, hexadecimal
To send Datagram, destination IP and MAc add of Destination Pc
must be Know
Protocol to determine/find MAc address in same subnet.
ARP table stores Mac address with IP add
ARP table
LAN
Default gateway
D2
D1
C
A
IP= 111-111-111-1
B
111-111-111-2
MAC = 71-65-F7-26-0B-53
Scenario1
Host A need to send pkt to Host B
IP
MAC TTL
A will look at his ARP table →
empty so send ARP query to all nodes
L>
source MAC : 71-65-...
Target IP : 111. . . . 2
send to FFF-FFF-FF
Src IP : 111. . . . 1
FF
B replies to A with ARP response, giving its MAc add
A receives response and save
B's MAC address in ARP table
Scenario 2/ Host A → Host C
Host sends to the MAC add of Default gateway D1
dest
Router receives frame, changes its dest MAC to Pc C and src MAC
as D2
```

## Page 42
### Bellman Ford
```text
Bellman Ford
L distance vector
```
