# Networking Cheatsheet

- [Networking Cheatsheet](#networking-cheatsheet)
  * [About](#about)
  * [Configuring IP Address on host](#configuring-ip-address-on-host)
  * [Reloading a host device](#reloading-a-host-device)
  * [Commands from host](#commands-from-host)
    + [ping](#ping)
    + [ipconfig /all](#ipconfig--all)
    + [tracert](#tracert)
  * [Lab 2a](#lab-2a)
    + [enable](#enable)
    + [configure terminal](#configure-terminal)
    + [show version](#show-version)
    + [show running-config](#show-running-config)
    + [hostname](#hostname)
    + [no ip domain-lookup](#no-ip-domain-lookup)
    + [banner motd](#banner-motd)
    + [show ip interface brief](#show-ip-interface-brief)
    + [show interface status](#show-interface-status)
  * [Lab 2b](#lab-2b)
    + [show interfaces](#show-interfaces)
    + [clear mac address-table](#clear-mac-address-table)
    + [show mac address-table](#show-mac-address-table)
  * [Lab 3a](#lab-3a)
    + [vlan](#vlan)
    + [config-vlan name](#config-vlan-name)
    + [show vlan](#show-vlan)
    + [show vlan brief](#show-vlan-brief)
    + [Assigning VLANs to switch interfaces](#assigning-vlans-to-switch-interfaces)
    + [Assigning VLANS to multiple interfaces.](#assigning-vlans-to-multiple-interfaces)
    + [Removing VLAN assignment from an interface.](#removing-vlan-assignment-from-an-interface)
    + [Remove VLAN ID from the VLAN database.](#remove-vlan-id-from-the-vlan-database)
    + [Initiate trunking on interface](#initiate-trunking-on-interface)
    + [show interfaces trunk](#show-interfaces-trunk)
  * [Lab 3b](#lab-3b)
    + [no shutdown](#no-shutdown)
    + [channel-group](#channel-group)
    + [show run interface](#show-run-interface)
    + [show interfaces](#show-interfaces-1)
    + [show etherchannel summary](#show-etherchannel-summary)
    + [Configuring trunk ports (EtherChannel)](#configuring-trunk-ports--etherchannel-)
    + [Configure LACP](#configure-lacp)
  * [Lab 4b](#lab-4b)
    + [Exporting Configurations from Cisco Packet Tracer](#exporting-configurations-from-cisco-packet-tracer)
    + [ip address](#ip-address)
    + [show ip interface brief](#show-ip-interface-brief-1)
    + [Setting up a interface's IP Address](#setting-up-a-interface-s-ip-address)
    + [Configuring a loopback interface](#configuring-a-loopback-interface)
  * [Lab 5b](#lab-5b)
    + [Configure HSRP](#configure-hsrp)


<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

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

## Lab 3a

### vlan
`vlan <n>`
- Requires **CONF T** mode to use.
- Create vlan `<n>` on the switch.

### config-vlan name
`name <name>`
- Requires **CONF T** and **VLAN** mode to use.
- Changes vlan name to `<name>` on the switch.

sample creating vlan:
```
S1(config)# vlan 10
S1(config-vlan)# name Student
```
### show vlan
`show vlan`
- Show list of VLANs on device.

sample output:
```
S1# show vlan
VLAN Name Status Ports
---- -------------------------------- --------- -------------------------------
1 default active Fa0/1, Fa0/2, Fa0/3, Fa0/4
Fa0/5, Fa0/6, Fa0/7, Fa0/8
Fa0/9, Fa0/10, Fa0/11, Fa0/12
Fa0/13, Fa0/14, Fa0/15, Fa0/16
Fa0/17, Fa0/18, Fa0/19, Fa0/20
Fa0/21, Fa0/22, Fa0/23, Fa0/24
Gi0/1, Gi0/2
10 Student active
20 Faculty active
1002 fddi-default act/unsup
1003 token-ring-default act/unsup
1004 fddinet-default act/unsup
1005 trnet-default act/unsup
VLAN Type SAID MTU Parent RingNo BridgeNo Stp BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1 enet 100001 1500 - - - - - 0 0
10 enet 100010 1500 - - - - - 0 0
20 enet 100020 1500 - - - - - 0 0
VLAN Type SAID MTU Parent RingNo BridgeNo Stp BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1002 fddi 101002 1500 - - - - - 0 0
1003 tr 101003 1500 - - - - - 0 0
1004 fdnet 101004 1500 - - - ieee - 0 0
1005 trnet 101005 1500 - - - ibm - 0 0
Remote SPAN VLANs
------------------------------------------------------------------------------
Primary Secondary Type Ports
------- --------- ----------------- ------------------------------------------ 

```
### show vlan brief
`show vlan br`
- Show VLAN mapping to interfaces.

sample output:
```
Switch>show vlan br

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                Fa0/9, Fa0/10, Fa0/11, Fa0/12
                                                Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                Fa0/17, Fa0/18, Fa0/19, Fa0/20
                                                Fa0/21, Fa0/22, Fa0/23, Fa0/24
                                                Gig0/1, Gig0/2
10   VLAN0010                         active    
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active 
```
### Assigning VLANs to switch interfaces
- Assign PC-A to the Student VLAN.

```
S1(config)# interface f0/6
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 10
```

### Assigning VLANS to multiple interfaces.
- Assign interface F0/11 - 24 to VLAN 10.

```
S1(config)# interface range f0/11-24
S1(config-if-range)# switchport mode access
S1(config-if-range)# switchport access vlan 10
S1(config-if-range)# end
```

### Removing VLAN assignment from an interface.
- Use the `no switchport access vlan` command to remove VLAN 10 assignment to F0/24.

```
S1(config)# interface f0/24
S1(config-if)# no switchport access vlan
S1(config-if)# end
```

### Remove VLAN ID from the VLAN database.
- Use the `no vlan 30` command to remove VLAN 30 from the VLAN database. 
- All ports associated with this VLAN will now not be associated with any VLAN...
```
S1(config)# no vlan 30
S1(config)# end
```

### Initiate trunking on interface
- Access interface, then use `switchport mode dynamic desirable` to convert interface to dynamic desirable mode. 
- Both switches need to have the approriate trunking mode for trunking to work...
- `switchport mode dynamic auto`, `switchport mode dynamic desirable`, `switchport mode access`, `switchport mode trunk`. (different modes) 
```
S1(config)# interface f0/1
S1(config-if)# switchport mode dynamic desirable
```

### show interfaces trunk
`show interfaces trunk`

- Views trunked interfaces.

sample output:
```
Port Mode Encapsulation Status Native vlan
Fa0/1 desirable 802.1q trunking 1
Port Vlans allowed on trunk
Fa0/1 1-4094
Port Vlans allowed and active in management domain
Fa0/1 1,10,20
Port Vlans in spanning tree forwarding state and not pruned
Fa0/1 1,10,20 
```

## Lab 3b

### no shutdown
`no shutdown`
- Requires **CONF T** mode to use.
- Requires **INTERFACE CONFIG MODE** to use.
- enables an interface (brings it up).

### channel-group
`channel-group <n> <mode>`

- Requires **CONF T** mode to use.
- Creates channel group for EtherChannel with selected mode
- modes:
    - desirable
    - auto

example output:
```
S1(config)# interface range g1/0/3-4
S1(config-if-range)# channel-group 1 mode desirable

Creating a port-channel interface Port-channel 1

S1(config-if-range)# no shutdown

S3(config)# interface range g1/0/3-4
S3(config-if-range)# channel-group 1 mode auto

Creating a port-channel interface Port-channel 1

S3(config-if-range)# no shutdown 
```

### show run interface
`show run interface <interface>`

- Displays interface configurations.

sample output:
```
S1# show run interface g1/0/3
Building configuration...
Current configuration : 70 bytes
!
Interface GigabitEthernet1/0/3
 channel-group 1 mode desirable
```

### show interfaces
`show interfaces <interface>`

- Displays curent interface information.

sample output:
```
FastEthernet0/1 is down, line protocol is down (disabled)
  Hardware is Lance, address is 00e0.f9cc.1801 (bia 00e0.f9cc.1801)
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

### show etherchannel summary
`show etherchannel sumamry`

- Displays etherchannel summary

sample output:
```
S1# show etherchannel summary
Flags: D - down P - bundled in port-channel
 I - stand-alone s - suspended
 H - Hot-standby (LACP only)
 R - Layer3 S - Layer2
 U - in use f - failed to allocate aggregator
 M - not in use, minimum links not met
 u - unsuitable for bundling
w - waiting to be aggregated
d - default port
Number of channel-groups in use: 1
Number of aggregators: 1
Group Port-channel Protocol Ports
------+-------------+-----------+-----------------------------------------------
1 Po1(SU) PAgP Gi1/0/3(P) Gi1/0/4(P)
```

### Configuring trunk ports (EtherChannel)
- After the ports have been aggregated, commands applied at the port channel interface affect all the links that were bundled together. Manually configure the Po1 ports on S1 and S3 as trunk ports. 

```
S1(config)# interface port-channel 1
S1(config-if)# switchport mode trunk
S3(config)# interface port-channel 1
S3(config-if)# switchport mode trunk 
```

### Configure LACP
- LACP is an open source protocol for link aggregation developed by the IEEE. In Part 3, the link between S1 and S2 will be configured using LACP. Also, the individual links will be configured as trunks before they are
bundled together as EtherChannels.

```
S1(config)# interface range g1/0/1-2
S1(config-if-range)# switchport mode trunk
S1(config-if-range)# channel-group 2 mode active
Creating a port-channel interface Port-channel 2
S1(config-if-range)# no shutdown
S2(config)# interface range g0/1-2
S2(config-if-range)# switchport mode trunk
S2(config-if-range)# channel-group 2 mode passive
Creating a port-channel interface Port-channel 2
S2(config-if-range)# no shutdown 
```

## Lab 4b

### Exporting Configurations from Cisco Packet Tracer
- On the Packet Tracer workspace, select the network device and then click on
the Config tab in the device configuration window.
- Next, click on the Export button to export the Running Config to a file, say
S1_running-config.txt. 
- Reload switch / Router.
- Remove each instance of --More-- if it exists. (on .txt file)
- Delete the initial lines so that the first line starts with the first configuration command as shown below: 
```
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption 
```
- Launch Tera Term and establish a console connection.
- Enter global config mode.
```
Switch> enable
Switch# configure terminal
Switch(config)# 
```
- From the Tera Term File menu, select Send file...
- Locate the configuration file S1_running-config.txt and select Open.
- Import is now in progress. When done, verify the running config and the VLAN
in the switch.


### ip address
`ip address <ip-adr> <mask>`
- Requires **CONF T** mode to use.
- Requires **INTERFACE CONFIG MODE** to use.
- Set specific interface's ip address, subnet mask

example:
```
R2(config-if)# ip address 192.168.1.1 255.255.255.0
```

### show ip interface brief
`show ip int br`
- Show router interfaces information.

example output:
```
R2# show ip interface brief
Interface IP-Address OK? Method Status Protocol
GigabitEthernet0/0/0 192.168.1.1 YES manual up up
GigabitEthernet0/0/1 unassigned YES unset administratively down down
Loopback0 209.165.200.225 YES manual up up
Vlan1 unassigned YES unset administratively down down
```

### Setting up a interface's IP Address

```
R2(config)# interface g0/0/0
R2(config-if)# description Connection to PC-A
R2(config-if)# ip address 192.168.1.1 255.255.255.0
R2(config-if)# no shutdown
R2(config-if)# exit
R2(config)# exit
R2#
```

### Configuring a loopback interface
To configure loopback interface, enter the commands as follows:

```
R2(config)# interface loopback 0
 or
R2(config)# interface lo0
R2(config-if)# ip address 209.165.200.225 255.255.255.224
```

## Lab 5b

### Configure HSRP
- Hot Standby Router Protocol is a Cisco proprietary redundancy protocol for establishing a fault-tolerant default gateway.
- Configure two or more routers as standby routers and only a single router as an active router. 
- All the routers in a single HSRP group shares a single MAC address and IP address, which acts as a default gateway to the local network.
- [HSRP version 1 VS version 2](https://www.ciscozine.com/why-use-hsrp-version-2/)
- On active router/L3 switch: 
```
D1(config)# interface vlan 1
D1(config-if)# standby version 2
D1(config-if)# standby 1 ip 192.168.1.254
D1(config-if)# standby 1 priority 150
D1(config-if)# standby 1 preempt
```
- Default priority of 100. Set higher priority for router to be the active router.
- Preempt needed for active router. In the case where active router is disabled and reconnected, active status will be automatically be re-established.
- On standby router/L3 switch:
```
D3(config)# interface vlan 1
D3(config-if)# standby version 2
D3(config-if)# standby 1 ip 192.168.1.254
```

### Verify HSRP status
`show standby`
- Check HSRP status

- example output:
```
D1#show standby
Vlan1 - Group 1 (version 2)
  State is Standby
    17 state changes, last state change 02:53:37
  Virtual IP address is 192.168.1.254
  Active virtual MAC address is 0000.0C9F.F001
    Local virtual MAC address is 0000.0C9F.F001 (v2 default)
  Hello time 3 sec, hold time 10 sec
    Next hello sent in 2.81 secs
  Preemption enabled
  Active router is 192.168.1.3, priority 200 (expires in 6 sec)
    MAC address is 0000.0C9F.F001
  Standby router is local
  Priority 150 (configured 150)
  Group name is hsrp-Vl1-1 (default)
```

`show standby brief`
- View HSRP status summary

- example output:
```
D1#show standby
Vlan1 - Group 1 (version 2)
  State is Standby
    17 state changes, last state change 02:53:37
  Virtual IP address is 192.168.1.254
  Active virtual MAC address is 0000.0C9F.F001
    Local virtual MAC address is 0000.0C9F.F001 (v2 default)
  Hello time 3 sec, hold time 10 sec
    Next hello sent in 2.81 secs
  Preemption enabled
  Active router is 192.168.1.3, priority 200 (expires in 6 sec)
    MAC address is 0000.0C9F.F001
  Standby router is local
  Priority 150 (configured 150)
  Group name is hsrp-Vl1-1 (default)
```