# End-to-End-IP-transmission
layer 3

Routing between two networks

What happens when a host(PC1) in one network wants to send ip packet to a host(PC2) in another network

STEP-1: PC1 finds out that PC2 is located in different network(by applying networ mask to the own and foreign IP address)

STEP-2: On network layer PC1 adds IP header with source IP - 12.16.3.7,destination IP - 192.168.1.15 and TTL - 64

STEP-3: PC1 checks local ARP table to find MAC address o the default gateway(if absent, sends ARP request)

STEP-4: On data-link layer PC1 adds ethernet header(source - a6:37:2b:5f:be:47 , dest - 31:a1:2c:1:3a:1b) & sends ethernet frame

STEP-5: Switch1 receives ethernet frame from PC1 on Fa0/3 interface, verifies FCS, checks MAC address tableto find where destiaion MAC is located and find its behind Gi1/1

STEP-6: Switch1 adds MAC address of PC1 to the MAC address table & maps it to the Fa0/3(if MAC of PC1 not yet in the table)

STEP-7: Switch1 sends ethernet frame toits Gi1/1(towards router Gi0/0 interface)

STEP-8: Router receives ethrnet frame on its Gi0/0 o datalink layer verifies FCS, checks destiation MAC address field & sees that MAC matches with MAC of its Gi0/0 interface

STEP-9: Router removes ethernet header & examines network layer IPv4 header, checks header checksum & TTL

STEP-10: Router sees that destination IP address in the IP packet 192.168.1.15 doesn't match with any of its own IP addresses. That's why router must send it further

STEP-11: Router checks routing table to find matching route for the 192.18.1.15 IP address. For eah route it applies network mask to the destination IP address & compares result to the prefix

STEP-12: Router sends ARP request for MAC address of the 192.168.1.15 IP address(if MAC of PC2 is absent i the ARP cache on the router). PC2 responds to this ARP request with its MAC 20:af:41:26:56:ab

STEP-13: On the network layer, router decrements TTL by one(it becomes 63 = 64-1) & calculates new IPv4 header checksum

STEP-14: On the data link layer router adds new ethernet header and calculates FCS

STEP-15: Router sends ethernet frame via Gi0/1 interface(according to the route in the routing table)

STEP-16: Switch2 rceives ethernet frame from router on Gi1/2 interface, verifies FCS, checks MAC address table to find where destination MAC is located & finds it behind Fa0/5

STEP-17: Switch-2 adds MAC addrss of router's Gi0/1 interface to the MAC address of router's Gi0/1 interface to the MAC address table & maps it to Gi1/2(if MAC of router not yet in table)

STEP-18: Switch2 sends ethenet frame to Fa0/5

STEP-19: PC2 receives frame & on the data link layer verifies FCS,compares destination MAC address to its own, finds they are equal, removes ethernet header 

STEP-20: On the network layr PC2 checks header checksum & TTL, compares destination IP to its own IP. They are equal, strips IPv4 header & sends segment to the transport layer for further processing
