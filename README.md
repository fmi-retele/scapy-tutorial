##### Requirements:
- use any linux or use the [Ubuntu x64 vbox machine](https://github.com/fmi-retele/vbox-scapy/releases/download/v1/osbox.vdi.tar.gz)
- check that you have [scapy](http://www.secdev.org/projects/scapy/) installed
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
