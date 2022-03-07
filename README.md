# Networking Cheatsheet

## About
This repository contains a collection of networking commands / notes for easier referencing in my networking module **(ICT 1010 Computer Networks)**.

## Configuring IP Address on host
- Go to Windows Start > Settings
- go to Network & Internet
- select Ethernet and then Change adapter options
- Right click Ethernet interface and select Properties.
- Select Internet Protocol Version 4 (TCP/IPv4) and click Properties.
- Change IP Address, Subnet mask, Default gateway.

## Reloading a host device
```
en
delete vlan.dat
erase startup-config
reload
```

- Issue the reload command to remove an old configuration from memory. When prompted to Proceed with reload, press Enter to confirm the reload. Pressing any other key will abort the reload.

```
Router# reload
Proceed with reload? [confirm]
*Nov 29 18:28:09.923: %SYS-5-RELOAD: Reload requested by console.
Reload Reason: Reload Command. 
```

- You may receive a prompt to save the running configuration prior to reloading the router. Respond by typing no and press Enter. 

```
System configuration has been modified. Save? [yes/no]: no
```

- After the router reloads, you are prompted to enter the initial configuration dialog. Enter no and press Enter.

```
Would you like to enter the initial configuration dialog? [yes/no]: no
```

- You will be prompted to terminate the autoinstall program. Respond yes and then press Enter.

```
Would you like to terminate autoinstall? [yes]: yes
```

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

## Lab 2a

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

## Lab 2b

### show interfaces
`show int <int>`
- Display MAC address information for specified port.

sample output:
```
Switch>show int f0/6
FastEthernet0/6 is down, line protocol is down (disabled)
  Hardware is Lance, address is 00e0.f9cc.1806 (bia 00e0.f9cc.1806)
 BW 100000 Kbit, DLY 1000 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  Keepalive set (10 sec)
  Half-duplex, 100Mb/s
  input flow-control is off, output flow-control is off
  ARP type: ARPA, ARP Timeout 04:00:00
  Last input 00:00:08, output 00:00:05, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0/0 (size/max/drops/flushes); Total output drops: 0
  Queueing strategy: fifo
  Output queue :0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     956 packets input, 193351 bytes, 0 no buffer
     Received 956 broadcasts, 0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
     0 watchdog, 0 multicast, 0 pause input
     0 input packets with dribble condition detected
     2357 packets output, 263570 bytes, 0 underruns
     0 output errors, 0 collisions, 10 interface resets
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier
     0 output buffer failures, 0 output buffers swapped out
```

### clear mac address-table 
`clear mac address-table dynamic`
- Requires **ENABLE** mode to use.
- Clears the dynamic (learned) MAC entries from the MAC address table.

### show mac address-table
`show mac address-table`
- Displays the current switch's mac address table.

sample output:
```
S1# show mac address-table
 Mac Address Table
-------------------------------------------
Vlan Mac Address Type Ports
---- ----------- -------- -----
 All 0100.0ccc.cccc STATIC CPU
 All 0100.0ccc.cccd STATIC CPU
 All 0180.c200.0000 STATIC CPU
 All 0180.c200.0001 STATIC CPU
 All 0180.c200.0002 STATIC CPU
 All 0180.c200.0003 STATIC CPU
 All 0180.c200.0004 STATIC CPU
 All 0180.c200.0005 STATIC CPU
 All 0180.c200.0006 STATIC CPU
 All 0180.c200.0007 STATIC CPU
 All 0180.c200.0008 STATIC CPU
 All 0180.c200.0009 STATIC CPU
 All 0180.c200.000a STATIC CPU
 All 0180.c200.000b STATIC CPU 
```
Add info here...

