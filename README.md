# End-to-End-IP-transmission
layer 3

Routing betweento networks

What happens when a host(PC1) in one network wants to send ip packet to a host(PC2) in another network

STEP-1: PC1 finds out that PC2 is located in different network(by applying networ mask to the own and foreign IP address)

STEP-2: On network layer PC1 adds IP header with source IP - 12.16.3.7,destination IP - 192.168.1.15 and TTL - 64

STEP-3: PC1 checks local ARP table to find MAC address o the default gateway(if absent, sends ARP request)

STEP-4: On data-link layer PC1 adds ethernet header(source - a6:37:2b:5f:be:47 , dest - 31:a1:2c:1:3a:1b) & sends ethernet frame

STEP-5: Switch1 receives ethernet frame from PC1 on Fa0/3 interface, verifies FCS, checks MAC address tableto find where destiaion MAC is located and find its behind Gi1/1

STEP-6: Switch1 ads
STEP-7:
STEP-8:
STEP-9:
STEP-10:
STEP-11:
STEP-12:
STEP-13:
STEP-14:
STEP-15:
STEP-16:
STEP-17:
STEP-18:
STEP-19:
STEP-20:
