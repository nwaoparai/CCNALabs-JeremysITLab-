1. Connect PC1's RS-232 port to R1's console port.

2. Use the console connection to configure the router from PC1.  Change the hostname to R1.

3. Set the enable secret of R1 to 'cisco'.

4. Set the console password of R1 to 'ccna', and make it required to connect to R1 by the console port.  Check the runing configuration.  Is the password encrypted?

5. Enable password encryption on R1.  Verify by checking the running configuration, and then save your configurations.

Router>en<br />
Router#config t<br />
Enter configuration commands, one per line.  End with CNTL/Z.<br />
Router(config)#hostname R1<br />
R1(config)#enable secret cisco<br />
R1(config)#line console 0<br />
R1(config-line)#password ccna<br />
R1(config-line)#end<br />
R1#<br />
%SYS-5-CONFIG_I: Configured from console by console<br />
<br />
R1#copy run start<br />
Destination filename [startup-config]? <br />
Building configuration...<br />
[OK]<br />
R1#exit<br />
<br />
R1>en<br />
Password: <br />
Password: <br />
R1#conf t<br />
Enter configuration commands, one per line.  End with CNTL/Z.<br />
R1(config)#line con 0<br />
R1(config-line)#login<br />
R1(config-line)#end<br />
R1#<br />
%SYS-5-CONFIG_I: Configured from console by console<br />
<br />
R1#copy run start<br />
Destination filename [startup-config]? <br />
Building configuration...<br />
[OK]<br />
R1#exit<br />
