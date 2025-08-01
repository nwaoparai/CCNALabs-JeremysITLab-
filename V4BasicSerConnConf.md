1. Use CDP  to discover which interfaces are used to connect the routers and switches.

2. Identify which end of the serial cable attaching R1 and R2 is DCE and which is DTE. 

3. Set the clock rate on the DCE end to 64 Kb/s.

4. Set the IP addresses of the serial interfaces of R1 and R2 to 192.168.0.1/24 and 192.168.0.2/24, respectively.

5. Ping between the routers to test connectivity.
<br />
SW1>en<br />
SW1#sh cdp neigh<br />
SW1#sh cdp neighbors<br /> 
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge<br />
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone<br />
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID<br />
R1           Fas 0/1          168            R       C810        Fas 0<br />
<br />
R1>en<br />
R1#conf t<br />
Enter configuration commands, one per line.  End with CNTL/Z.<br />
R1(config)#int s0<br />
R1(config-if)#no shut<br />
<br />
%LINK-5-CHANGED: Interface Serial0, changed state to down<br />
R1(config-if)#end<br />
R1#<br />
%SYS-5-CONFIG_I: Configured from console by console<br />
<br />
%LINK-5-CHANGED: Interface Serial0, changed state to up<br />
<br />
R2>en<br />
R2#conf t<br />
Enter configuration commands, one per line.  End with CNTL/Z.<br />
R2(config)#int s0<br />
R2(config-if)#no shut<br />
<br />
R2(config-if)#<br />
%LINK-5-CHANGED: Interface Serial0, changed state to up<br />
<br />
R2(config-if)#<br />
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0, changed state to up<br />
<br />
R1#sh cdp ne<br />
R1#sh cdp neighbors <br />
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge<br />
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone<br />
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID<br />
SW1          Fas 0            143            S       2960        Fas 0/1<br />
R2           Ser 0            131            R       C810        Ser 0<br />
<br />
R2#sh cdp nei<br />
R2#sh cdp neighbors <br />
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge<br />
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone<br />
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID<br />
SW2          Fas 0            162            S       2960        Fas 0/1<br />
R1           Ser 0            141            R       C810        Ser 0<br />
<br />
SW2>en<br />
SW2#sh cdp nei<br />
SW2#sh cdp neighbors <br />
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge<br />
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone<br />
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID<br />
R2           Fas 0/1          147            R       C810        Fas 0<br />
<br />
R1#show controllers serial 0<br />
Interface Serial0<br />
Hardware is PowerQUICC MPC860<br />
**DCE V.35, clock rate 2000000**<br />
idb at 0x81081AC4, driver data structure at 0x81084AC0<br />
SCC Registers:<br />
General [GSMR]=0x2:0x00000000, Protocol-specific [PSMR]=0x8<br />
<br />
R1(config)#int s0<br />
R1(config-if)#clock rate 64000<br />
R1(config-if)#ip address 192.168.0.1 255.255.255.0<br />
<br />
R2#conf t<br />
Enter configuration commands, one per line.  End with CNTL/Z.<br />
R2(config)#int s0<br />
R2(config-if)#ip address 192.168.0.2 255.255.255.0<br />
<br />
R2#ping 192.168.0.1<br />
<br />
Type escape sequence to abort.<br />
Sending 5, 100-byte ICMP Echos to 192.168.0.1, timeout is 2 seconds:<br />
!!!!!<br />
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/13/26 ms<br />
<br />
%LINEPROTO-5-UPDOWN: Line protocol on Interface Serial0, changed state to up<br />
