1. Connect the two routers by their GigabitEthernet0/0 interfaces

2. Set the hostname of each router according to the network diagram (R1 and R2)

3. Set the enable password of each router to 'cisco'

4. Set the enable secret of each router to 'ccna'

5. Exit back to exec mode and try to enter privileged exec mode.  Which password do you have to use?

6. View the running configuration.  Which of the passwords is encrypted?

7. Enable password encryption on the router, and view the running configuration.  What has changed?

8. Save the configuration and reload the router to confirm.

Router>enable<br/>
Router#config t<br/>
Enter configuration commands, one per line.  End with CNTL/Z.<br/>
Router(config)#hostname R1<br/>
R1(config)#enable password cisco<br/>
R1(config)#do sh run<br/>
Building configuration...<br/>
<br/>
Current configuration : 643 bytes<br/>
!<br/>
version 15.1<br/>
no service timestamps log datetime msec<br/>
no service timestamps debug datetime msec<br/>
no service password-encryption<br/>
!<br/>
hostname R1<br/>
!<br/>
!<br/>
!<br/>
enable password cisco<br/>
!<br/>
!<br/>
!<br/>

<br/>
R1(config)#enable secret ccna<br/>
R1(config)#exit<br/>
R1#<br/>
%SYS-5-CONFIG_I: Configured from console by console

R1#copy run start
Destination filename [startup-config]? 
Building configuration...
[OK]
R1#exit

R1#config t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#do sh run
Building configuration...

Current configuration : 690 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname R1
!
!
!
enable secret 5 $1$mERr$Bok4KDfVutXOJolNq009M/
enable password cisco
R1(config)#service pass
R1(config)#service password-encryption 
R1(config)#do sh run
Building configuration...

Current configuration : 696 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R1
!
!
!
enable secret 5 $1$mERr$Bok4KDfVutXOJolNq009M/
enable password 7 0822455D0A16
!
!
!
!
!
!
ip cef
no ipv6 cef
