1. Connect R1 and R2 by their GigabitEthernet0/0 interfaces

2. Set the hostnames according to the network diagram (R1 and R2)

3. Set the enable password on each router to 'cisco'

4. View the password in the running configuration.  Is it encrypted?

5. Enable password encryption on each router

6. View the password in the running configuration.  Is it encrypted?

7. Disable password encryption on each router.

8. View the password in the running configuration.  Is it encrypted?

Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname R1
R1(config)#enable password cisco
R1(config)#exit
R1#
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#service passwor
R1(config)#service password-encryption 
R1(config)#do sh run
!
hostname R1
!
!
!
enable password 7 0822455D0A16
R1(config)#no service pa
R1(config)#no service password-encryption 
R1#sh run
Building configuration...

Current configuration : 655 bytes
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
enable password 7 0822455D0A16
