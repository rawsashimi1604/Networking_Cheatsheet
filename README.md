# Networking Cheatsheet

## About
This repository contains a collection of networking commands / notes for easier referencing in my networking module **(ICT 1010 Computer Networks)**.

## Commands from host

### ping
`ping <-t> <ip address>`
- Specify `-t` to continue sending echo Request messages to the destination until interrupted. 

### ipconfig /all
`ipconfig /all`
- Shows all information about network adapters (IP Address, Default Gateway, Subnet Mask, MAC Address etc..)

### tracert
`tracert <ip address>`
- Trace the route a data packet takes before reaching its destination, displaying information on each hop along the route.

### reload
`delete vlan.dat`
`erase startup-config`
`reload`
- To erase startup config and reboot routers.

## Lab 2a
>>>>>>> 61c8cb318553f7526100ad363bf3b3ad1fa4f2ee

### enable
`en`
- Changes to enable mode.

### configure terminal
`config t`
- Changes to config t mode.

### show version
`show version`
- Shows Cisco IOS version information of the switch.

### show running-config
`show running-config`
- Requires **ENABLE** mode to use.
- Show existing running configuration of the switch.

### hostname
`hostname <name>`
- Requires **CONFIG T** mode to use. 
- Changes switch hostname to `<name>`.

### no ip domain-lookup
`no ip domain-lookup`
- Requires **CONFIG T** mode to use. 
- Prevents the switch from attempting to translate incorrectly entered commands as though they were hostnames

### banner motd #
`banner motd #`
`<text> #`
- Requires **CONFIG T** mode to use. 
- Creates message of the day (MOTD) banner. Requires delimited (#) to identify the end of the message.

### show ip interface brief
`show ip int br`
- Displays the states of the interfaces on the switch.
- Shows 2 code version (layer 1 + layer 2)
- Layer 1 => line status 
- Layer 2 => protocol status 

sample output:
```
Switch>show ip int br
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual down                  down 
FastEthernet0/2        unassigned      YES manual down                  down 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual down                  down 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual down                  down 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  unassigned      YES manual administratively down down
```

### show interface status
`show interface status`
- Requires **ENABLE** mode to use.
- Shows one-code status (layer 1)

sample output:
```
Switch#show interface status
Port      Name               Status       Vlan       Duplex  Speed Type
Fa0/1                        notconnect   1          auto    auto  10/100BaseTX
Fa0/2                        notconnect   1          auto    auto  10/100BaseTX
Fa0/3                        notconnect   1          auto    auto  10/100BaseTX
Fa0/4                        notconnect   1          auto    auto  10/100BaseTX
Fa0/5                        notconnect   1          auto    auto  10/100BaseTX
Fa0/6                        notconnect   1          auto    auto  10/100BaseTX
Fa0/7                        notconnect   1          auto    auto  10/100BaseTX
Fa0/8                        notconnect   1          auto    auto  10/100BaseTX
Fa0/9                        notconnect   1          auto    auto  10/100BaseTX
Fa0/10                       notconnect   1          auto    auto  10/100BaseTX
Fa0/11                       notconnect   1          auto    auto  10/100BaseTX
Fa0/12                       notconnect   1          auto    auto  10/100BaseTX
Fa0/13                       notconnect   1          auto    auto  10/100BaseTX
Fa0/14                       notconnect   1          auto    auto  10/100BaseTX
Fa0/15                       notconnect   1          auto    auto  10/100BaseTX
Fa0/16                       notconnect   1          auto    auto  10/100BaseTX
Fa0/17                       notconnect   1          auto    auto  10/100BaseTX
Fa0/18                       notconnect   1          auto    auto  10/100BaseTX
Fa0/19                       notconnect   1          auto    auto  10/100BaseTX
Fa0/20                       notconnect   1          auto    auto  10/100BaseTX
Fa0/21                       notconnect   1          auto    auto  10/100BaseTX
Fa0/22                       notconnect   1          auto    auto  10/100BaseTX
Fa0/23                       notconnect   1          auto    auto  10/100BaseTX
Fa0/24                       notconnect   1          auto    auto  10/100BaseTX
Gig0/1                       notconnect   1          auto    auto  10/100BaseTX
Gig0/2                       notconnect   1          auto    auto  10/100BaseTX
```
Add info here...

