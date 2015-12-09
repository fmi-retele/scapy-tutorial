## Requirements:
- use any linux or use the [Ubuntu x64 vbox machine](https://github.com/fmi-retele/vbox-scapy/releases/download/v1/osbox.vdi.tar.gz)
- check that you have [scapy](http://www.secdev.org/projects/scapy/) installed
- [scapy docs](www.secdev.org/projects/scapy/doc/usage.html)
- check additional [scapy resources](https://thepacketgeek.com/scapy-p-11-scapy-resources/)

### View different protocol headers 

```
import scapy
from scapy.all import DHCP, ARP, BOOTP, Ether, UDP, TCP, IP
```

#### Data link layer
- [ethernet] (http://www.networksorcery.com/enp/protocol/ethernet.htm)
```
ethernet = Ether()
ethernet.show()
```

#### Network layer
- [ARP] (http://www.networksorcery.com/enp/protocol/ARP.htm)
```
arp = ARP()
arp.show()
```

- [IP](http://www.networksorcery.com/enp/protocol/IP.htm)
```
ip = IP()
ip.show()
```

#### Transport layer
- [UDP](http://www.networksorcery.com/enp/protocol/UDP.htm)
```
udp = UDP()
udp.show()
```
- [TCP](http://www.networksorcery.com/enp/protocol/TCP.htm)
```
tcp = TCP()
tcp.show()
```

#### Application layer
- [BOOTP and DHCP headers](http://www.networksorcery.com/enp/protocol/DHCP.htm)
```
bootp = BOOTP()
bootp.show()
dhcp = DHCP()
dhcp.show()
```

#### Send functions @ data link layer
The [sendp()](http://www.secdev.org/projects/scapy/doc/usage.html#sending-packets) function will work at layer 2. It’s up to you to choose the right interface and the right link layer protocol.
- sendp            : Send packets at layer 2
- srp              : Send and receive packets at layer 2
- srp1             : Send and receive packets at layer 2 and return only the first answer
- srploop          : Send a packet at layer 2 in loop and print the answer each time
```
sendp(Ether()/IP(dst="1.2.3.4",ttl=(1,4)), iface="eth1")
answered, unanswered = srp(Ether(dst="ff:ff:ff:ff:ff:ff")/ARP(pdst="192.168.1.0/24"),timeout=2)
```

#### Send functions @ network layer
The [send()](http://www.secdev.org/projects/scapy/doc/usage.html#sending-packets) will send packets at layer 3. That is to say it will handle routing and layer 2 for you.
- send             : Send packets at layer 3
- sr               : Send and receive packets at layer 3
- sr1              : Send packets at layer 3 and return only the first answer
- srloop           : Send a packet at layer 3 in loop and print the answer each time
```
send(IP(dst="1.2.3.4")/ICMP())
answered, unanswered = sr(IP(dst="192.168.*.1-10")/UDP(dport=0))
```

