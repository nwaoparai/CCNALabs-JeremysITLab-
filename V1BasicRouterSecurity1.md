1. Connect R1 and R2 by their GigabitEthernet0/0 interfaces

2. Set the hostnames according to the network diagram (R1 and R2)

3. Set the enable password on each router to 'cisco'

4. View the password in the running configuration.  Is it encrypted?

5. Enable password encryption on each router

6. View the password in the running configuration.  Is it encrypted?

7. Disable password encryption on each router.

8. View the password in the running configuration.  Is it encrypted?

Router>enable<br />
Router#configure terminal<br />
Enter configuration commands, one per line.  End with CNTL/Z.<br />
Router(config)#hostname R1<br />
R1(config)#enable password cisco<br />
R1(config)#exit<br />
R1#<br />
R1#conf t<br />
Enter configuration commands, one per line.  End with CNTL/Z.<br />
R1(config)#service passwor<br />
R1(config)#service password-encryption <br />
R1(config)#do sh run<br />
!<br />
hostname R1<br />
!<br />
!<br />
!<br />
enable password 7 0822455D0A16<br />
R1(config)#no service pa<br />
R1(config)#no service password-encryption <br />
R1#sh run<br />
Building configuration...<br />
<br />
Current configuration : 655 bytes<br />
!<br />
version 15.1<br />
no service timestamps log datetime msec<br />
no service timestamps debug datetime msec<br />
no service password-encryption<br />
!<br />
hostname R1<br />
!<br />
!<br />
!<br />
enable password 7 0822455D0A16
