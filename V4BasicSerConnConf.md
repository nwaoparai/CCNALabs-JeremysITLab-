1. Use CDP  to discover which interfaces are used to connect the routers and switches.

2. Identify which end of the serial cable attaching R1 and R2 is DCE and which is DTE. 

3. Set the clock rate on the DCE end to 64 Kb/s.

4. Set the IP addresses of the serial interfaces of R1 and R2 to 192.168.0.1/24 and 192.168.0.2/24, respectively.

5. Ping between the routers to test connectivity.

SW1>en
SW1#sh cdp neigh
SW1#sh cdp neighbors 
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
R1           Fas 0/1          168            R       C810        Fas 0

R1>en
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#int s0
R1(config-if)#no shut

%LINK-5-CHANGED: Interface Serial0, changed state to down
R1(config-if)#end
R1#
%SYS-5-CONFIG_I: Configured from console by console

%LINK-5-CHANGED: Interface Serial0, changed state to up

R2>en
R2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R2(config)#int s0
R2(config-if)#no shut

R2(config-if)#
%LINK-5-CHANGED: Interface Serial0, changed state to up

R2(config-if)#
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0, changed state to up

R1#sh cdp ne
R1#sh cdp neighbors 
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
SW1          Fas 0            143            S       2960        Fas 0/1
R2           Ser 0            131            R       C810        Ser 0

R2#sh cdp nei
R2#sh cdp neighbors 
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
SW2          Fas 0            162            S       2960        Fas 0/1
R1           Ser 0            141            R       C810        Ser 0

SW2>en
SW2#sh cdp nei
SW2#sh cdp neighbors 
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
R2           Fas 0/1          147            R       C810        Fas 0

R1#show controllers serial 0
Interface Serial0
Hardware is PowerQUICC MPC860
**DCE V.35, clock rate 2000000**
idb at 0x81081AC4, driver data structure at 0x81084AC0
SCC Registers:
General [GSMR]=0x2:0x00000000, Protocol-specific [PSMR]=0x8

R1(config)#int s0
R1(config-if)#clock rate 64000
R1(config-if)#ip address 192.168.0.1 255.255.255.0

R2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R2(config)#int s0
R2(config-if)#ip address 192.168.0.2 255.255.255.0

R2#ping 192.168.0.1

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.0.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/13/26 ms

%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0, changed state to up
