- [Lab Sheet Cheat Sheet](#lab-sheet-cheat-sheet)
  - [Basic Configurations](#basic-configurations)
    - [Disable DNS Lookup](#disable-dns-lookup)
    - [Change Hostname](#change-hostname)
  - [Configuring VLANs & Trunking](#configuring-vlans--trunking)
    - [Create VLAN on S1](#create-vlan-on-s1)
    - [Check VLAN List](#check-vlan-list)
    - [Assigning VLAN to interfaces](#assigning-vlan-to-interfaces)
    - [Verify VLAN](#verify-vlan)
    - [Assign VLAN to multiple interfaces](#assign-vlan-to-multiple-interfaces)
    - [Remove VLAN assignment from an interface](#remove-vlan-assignment-from-an-interface)
    - [Remove VLAN ID from VLAN database](#remove-vlan-id-from-vlan-database)
  - [Configuring 802.1Q Trunk between switches](#configuring-8021q-trunk-between-switches)
    - [Negotiate Trunk Mode](#negotiate-trunk-mode)
    - [Check interface trunk](#check-interface-trunk)
    - [Manually configure trunk interface](#manually-configure-trunk-interface)
  - [Configure Etherchannel](#configure-etherchannel)
    - [Configuring PAgP on S1 and S3](#configuring-pagp-on-s1-and-s3)
    - [Verify that ports have been aggregated](#verify-that-ports-have-been-aggregated)
    - [Configure Trunk ports (Etherchannel)](#configure-trunk-ports-etherchannel)
    - [Configure LACP on S1, S2](#configure-lacp-on-s1-s2)
  - [Getting to know Integrated Services Routers(ISR)](#getting-to-know-integrated-services-routersisr)
    - [Show router IOS](#show-router-ios)
    - [Router reload](#router-reload)
  - [Simple Switch and router network](#simple-switch-and-router-network)
    - [Configure IP addresses on interfaces](#configure-ip-addresses-on-interfaces)
    - [Configure loopback interfaces](#configure-loopback-interfaces)
    - [Check interface configurations](#check-interface-configurations)
  - [Inter-VLAN Routing 802.1Q (Router on a stick)](#inter-vlan-routing-8021q-router-on-a-stick)
    - [Configure a subinterface for VLAN 10](#configure-a-subinterface-for-vlan-10)
  - [Layer 3 switch inter-VLAN routing](#layer-3-switch-inter-vlan-routing)
    - [Configure a Switched Virtual Interface (SVI) for VLAN 10](#configure-a-switched-virtual-interface-svi-for-vlan-10)
    - [Enable IP Routing on Layer 3 switch](#enable-ip-routing-on-layer-3-switch)
    - [Configure Layer 3 switch to behave like a router port](#configure-layer-3-switch-to-behave-like-a-router-port)
  - [Configuring IPv4 and Default Routes](#configuring-ipv4-and-default-routes)
    - [Configure Recursive Static route](#configure-recursive-static-route)
    - [Configure directly connected static route](#configure-directly-connected-static-route)
    - [Configure default route](#configure-default-route)
  - [Configuring HSRP](#configuring-hsrp)
    - [Configure HSRP on D1](#configure-hsrp-on-d1)
    - [Configure HSRP on D3](#configure-hsrp-on-d3)
    - [Verify HSRP](#verify-hsrp)
    - [Change HRSP Priority](#change-hrsp-priority)
  - [Configure Static and Dynamic NAT](#configure-static-and-dynamic-nat)
    - [Create a simulated web server on ISP](#create-a-simulated-web-server-on-isp)
    - [Configure static mapping](#configure-static-mapping)
    - [Specify the interfaces](#specify-the-interfaces)
    - [Verify NAT](#verify-nat)
    - [Configure Dynamic NAT](#configure-dynamic-nat)
      - [Clear NATs](#clear-nats)
    - [Define Access Control List (ACL) that matches the LAN IP address range](#define-access-control-list-acl-that-matches-the-lan-ip-address-range)
    - [Define the pool of usable public IP address](#define-the-pool-of-usable-public-ip-address)
    - [Define NAT from inside source list to the outside pool](#define-nat-from-inside-source-list-to-the-outside-pool)
  - [NAT Pool Overload](#nat-pool-overload)
  - [PAT](#pat)
  - [OSPF](#ospf)
    - [Configure OSPF on R1](#configure-ospf-on-r1)
    - [Configure the network statements for the networks on R1](#configure-the-network-statements-for-the-networks-on-r1)
    - [Verify OSPF](#verify-ospf)
    - [Change Router ID Assignment](#change-router-id-assignment)
    - [Change router using loopback addresses](#change-router-using-loopback-addresses)
    - [Change Router ID](#change-router-id)
    - [Configure OSPF Passive interface](#configure-ospf-passive-interface)
    - [Set passive interface as the default on a router](#set-passive-interface-as-the-default-on-a-router)
    - [Remove passive interface](#remove-passive-interface)
  - [Change OSPF Metrics](#change-ospf-metrics)
    - [Change Reference bandwidth](#change-reference-bandwidth)
    - [Change bandwidth](#change-bandwidth)
    - [Change Link Cost](#change-link-cost)

# Lab Sheet Cheat Sheet

## Basic Configurations
### Disable DNS Lookup
- `no ip domain-lookup`

### Change Hostname
- `hostname <HOSTNAME>`

## Configuring VLANs & Trunking

### Create VLAN on S1
```
vlan 10
name Student
vlan 20
name Faculty
```
### Check VLAN List
- `show vlan`

### Assigning VLAN to interfaces
```
interface f0/6
switchport mode access
switchport access vlan 10
```

### Verify VLAN
- `show vlan brief`

### Assign VLAN to multiple interfaces
```
interface range f0/11-24
switchport mode access
switchport access vlan 10
end
```

### Remove VLAN assignment from an interface
```
interface f0/24
no switchport access vlan
end
```

### Remove VLAN ID from VLAN database
```
no vlan 30
end
```

## Configuring 802.1Q Trunk between switches

### Negotiate Trunk Mode
```
interface f0/1
switchport mode dynamic desirable
```

- Use `vlan brief` to check configurations (Does not show in vlan table)

### Check interface trunk
- `show interfaces trunk`

### Manually configure trunk interface
```
interface f0/1
switchport mode trunk
```

## Configure Etherchannel
### Configuring PAgP on S1 and S3
- On S1
```
interface range g1/0/3-4
channel-group 1 mode desirable
no shutdown
```

- On S3
```
interface range g1/0/3-4
channel-group 1 mode auto
no shutdown
```

- To check:
  - `show run interface g1/0/3`
  - `show interfaces g1/0/3 switchport`

### Verify that ports have been aggregated
- `show etherchannel summary`

### Configure Trunk ports (Etherchannel)
- On S1 and S3
```
interface port-channel 1
switchport mode trunk
```

### Configure LACP on S1, S2
- On S1
```
interface range g1/0/1-2
switchport mode trunk
channel-group 2 mode active
no shutdown
```
- On S2
```
interface range g1/0/1-2
switchport mode trunk
channel-group 2 mode passive
no shutdown
```
## Getting to know Integrated Services Routers(ISR)

### Show router IOS
- `show version`

### Router reload
```
del vlan.dat
erase startup-config
reload
```


## Simple Switch and router network
### Configure IP addresses on interfaces
```
interface g0/0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
end
```

### Configure loopback interfaces 
```
interface lo0 or loopback 0
ip address 127.1.1.1 255.255.255.0
```

### Check interface configurations
- `show ip interface brief`

## Inter-VLAN Routing 802.1Q (Router on a stick)
### Configure a subinterface for VLAN 10
```
interface g0/1.10
encapsulation dot1q 10
ip address 1.1.1.1 255.255.255.0
```
- After adding the subinterfaces, turn on the main (physical interface)
```
interface g0/1
no shutdown
```

## Layer 3 switch inter-VLAN routing
### Configure a Switched Virtual Interface (SVI) for VLAN 10
```
interface vlan 10
ip address 1.1.1.1 255.255.255.0
no shutdown
exit
```

### Enable IP Routing on Layer 3 switch
- `ip routing`

- To check connectivity
  - `show ip route`

### Configure Layer 3 switch to behave like a router port
```
interface g0/0/0
no switchport
ip address 1.1.1.1 255.255.255.0
no shut
exit 
ip routing
```

## Configuring IPv4 and Default Routes
### Configure Recursive Static route
- `ip route <network address> <subnet mask> <ip-address>`
  - To remove, use the same command with starting with `no`

### Configure directly connected static route
- `ip route <network address> <subnet mask> <exit interface>`

### Configure default route
-`ip route 0.0.0.0 0.0.0.0 <ip address or exit interface>`

## Configuring HSRP
### Configure HSRP on D1
- On D1
```
interface vlan 1
standby version 2
standby 1 ip 192.168.1.254
standby 1 priority 150
standby 1 preempt 
```

### Configure HSRP on D3
- On D3
```
interface vlan 1
standby version 2
standby 1 ip 192.168.1.254
```

### Verify HSRP 
- `show standby`
- `show standby brief`

### Change HRSP Priority
```
interface g0/0
standby 1 priority 200
```

## Configure Static and Dynamic NAT

### Create a simulated web server on ISP
```
username webuser privilege 15 secret webpass
ip http server
ip http authentication local
```

### Configure static mapping
- `ip nat inside source static <private address> <public address>`
  - To remove static NAT mapping:
    - Add a `no` in front of the command

### Specify the interfaces
```
interface g0/1
ip nat inside
interface g0/0
ip nat outside
```

### Verify NAT 
- `show ip nat translation`
- `show ip nat statistics`

### Configure Dynamic NAT
- Firstly need to clear NATs

#### Clear NATs
```
clear ip nat translation *
clear ip nat statistics
```

### Define Access Control List (ACL) that matches the LAN IP address range
- `access-list 1 permit 192.168.1.0 0.0.0.255`

### Define the pool of usable public IP address
- `ip nat pool public_access <public address start range> <public address end range> netmask <subnet mask>`
  - Example:
    - `ip nat pool public_access 209.165.200.242 209.165.200.254 netmask 255.255.255.224`

### Define NAT from inside source list to the outside pool
- `ip nat inside source list 1 pool public_access`

## NAT Pool Overload
- Same configuration as dynamic NAT except the last line
  - `ip nat inside source list 1 pool public_access overload`
- Then specify the interfaces accordingly:
  - `ip nat inside`
  - `ip nat outside`

## PAT 
- Same setting of the NAT pool overload
- Remove the pool of usable public IP addresses
  - `no ip nat pool public_access 209.165.200.225 209.165.200.230 netmask 255.255.255.248`
- Remove the NAT translation from source list to outside pool
  - `no ip nat inside source list 1 pool public_access overload`
- Associate the source list with the outside interface
  - `ip nat inside source list 1 interfaces g0/0 overload`

## OSPF
### Configure OSPF on R1
- `router ospf 1`
  - Note: the OSPF process ID is kept locally and has no meaning to other routers on the network

### Configure the network statements for the networks on R1
```
network 192.168.1.0 0.0.0.255 area 0
network 192.168.12.0 0 0.0.0.3 area 0
network 192.168.13.0 0.0.0.255 area 0
```

### Verify OSPF
- To view neighbours
  - `show ip ospf neighbour`
- To view OSPF route
  - `show ip route`
- To view ip protocols
  - `show ip protocols`
- To view OSPF process information
  - `show ip ospf`
- To view summary of OSPF-enabled interfaces
  - `show ip ospf interface brief`
  - for more details:
    - `show ip ospf interface`
### Change Router ID Assignment
### Change router using loopback addresses
```
interface lo0
ip address 1.1.1.1 255.255.255.255
end
```
### Change Router ID
```
router ospf 1
router-id 11.11.11.11
end
```

### Configure OSPF Passive interface
```
router ospf 1
passive-interface g0/2
show ip ospf interface g0/2
```

### Set passive interface as the default on a router
```
router ospf 1
passive-interface default
```

### Remove passive interface
```
router ospf 1
no passive-interface g0/0
```
## Change OSPF Metrics
### Change Reference bandwidth
```
router ospf 1
auto-cost reference-bandwidth 10000
show ip ospf interface g1/0/3       // To check the cost
```

### Change bandwidth
```
interface g0/0
bandwidth 128
```

### Change Link Cost
```
interface g0/1
ip ospf cost 1565
```