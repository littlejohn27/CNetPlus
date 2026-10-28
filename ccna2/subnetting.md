Re-do DAY 1: 
Coretaas:        Corebaba:      CUCM:         EDGE

: 3-33           :37-71       :187-204      :364-389
: 77-84          :77-84       :207-220      :396-404
                 :100-126     :223-262      
                 :130-168     :265-276
                 :171-180     :278-283
                 :407-413     :286-358
                              :416-420

DAY2: 
CIDR: classless interdomain routing
/1 = 128.0.0.0
/2 = 192.0.0.0


task3: how to get consulatant/level skills
hayup level: 

pera:          ipv4:           ipv6:
0-9            0-255          0-9,a-f

3999      3.255.255.255       3fff
4000        4.0.0.0          :4000:
4001        4.0.0.1           4001

6999       6.255.255.255       6fff  
7000         7.0.0.0          :7000:
7001         7.0.0.1           7001

3097      3.0.255.253           30fd
3098      3.0.255.254           30fe
3099       3.0.255.255          30ff
3100       3.1.0.0              3100
 
6908        6.255.0.254       6f0e
6909        6.255.0.255       6f0f
6910        6.255.1.0         6f10  

3989       3.255.254.255     3fef
3990       3.255.255.0       3ff0
3991       3.255.255.1       3ff1

/25  = x.x.x.128  =  (4th , 128i )
/28   =   255.255.255.240 =  ( 4 , 16i )
/ 23  =  x.x.254.0        = (3,2i )  
TASK4: Bit Length:

195 = 8b
13 =  4b
1750 = 11b
855 =  10b
2,700 =  12b
2 =  2b
376 =  9b
888 = 10b
8 = 4b
212 = 8b 
4,500 = 13b
81 = 7b
8,500  = 14b  
55 = 6b

/27 =                     = (  ,  )
/   =  255.255.252.0      = (  ,  )
                          = (4th ,8i  )

6908         6.255.0.254       6f0e 
6909         6.255.0.255       6f0f
6910         6.255.1.0         6f10

task5: Job roles.

--------------------------------

19   = 5
6769 = 13
2000 = 11 
67   = 7
1025 = 11


/25 =  255.255.255.128    = (4th, 128i)
/21  =  255.255.248.0     = (3rd ,8  )
/18  =  255.255.192.0     = (3th ,64i)

TASK6: SUBNETTING THE NOC FOR MSP: accenture:
worldMethod: 5-10mins vs rivanmethod: 3sec- Csi
10.0.0.0/8 --> 16,777,214 hosts:
       accenture         chevon      shell         fuelSave       caltex
           100host         1500       2800         350         950
convert     7b             11b        12b          9bits        10b      
subract032   /25           /21         /20         /23          /22
ipasok     4th,128i        3rd,8i     3rd,16i      3rd,2i      3rd,4i
NetAdd:  10.0.0.128/25   10.0.8.0/21 10.0.16.0/20  10.0.2.0/23 10.0.4.0/22
1stIP:   10.0.0.129       10.0.8.1     10.0.16.1    10.0.2.1    10.0.4.1
Last/bc: 10.0.0.255      10.0.15.255   10.0.31.255  10.0.3.255  10.0.7.255
NextNet:  10.0.1.0/?     10.0.16.0/?  10.0.32.0/?  10.0.4.0/?  10.0.8.0/? 

IMPLEMENT THE NETWORK DESIGN:
@C1:
Config t
vlan 20
name ACCENTURE.COM
Interface vlan 20
 desc ACCENTURE.COM
 no shut
 ip add 10.0.0.129 255.255.255.128
ip dhcp excluded-add 10.0.0.129 10.0.0.139
ip dhcp pool ACCENTURE.COM
 network 10.0.0.128 255.255.255.128
 default-router 10.0.0.129
 domain-name ACCENTURE.COM
Int e1/0
 no shut
 switchport mode access
 switchport access vlan 20
@S1
config t
int e1/0
no shut
ip add dhcp
do bp
******** FOR CHEVRON CLIENT:******
@C1:
Config t
vlan 21
name CHEVRON.COM
Interface vlan 21
 desc CHEVRON.COM
 no shut
 ip add 10.0.8.1 255.255.248.0
ip dhcp excluded-add 10.0.8.1 10.0.8.100
ip dhcp pool CHEVRON.COM
 network 10.0.8.0 255.255.248.0
 default-router 10.0.8.1
 domain-name CHEVRON.COM
@a1:
CONFIG T
Int e0/0
 no shut
 switchport mode access
 switchport access vlan 21
 DO SH VLAN BRIEF
@P1: 30S
config t
int e0/0
no shut
ip add dhcp
do bp
do sh ip domain

******** FOR shell CLIENT:******
@C1:
Config t
vlan 22
name SHELL.COM
Interface vlan 22
 desc SHELL.COM
 no shut
 ip add 10.0.16.1 255.255.240.0
ip dhcp excluded-add 10.0.16.1 10.0.16.100
ip dhcp pool SHELL.COM
 network 10.0.16.0 255.255.240.0
 default-router 10.0.16.1
 domain-name SHELL.COM
 do sh run | sec dhcp
@a2:
CONFIG T
Int e1/0
 no shut
 switchport mode access
 switchport access vlan 22
 DO SH VLAN BRIEF
@P2: 30S
config t
int e1/0
no shut
ip add dhcp
do bp
do sh ip domain

******** FOR fuelsave.com CLIENT:******
@C1:
Config t
vlan 23
name FUELSYET.COM
Interface vlan 23
 desc FUELSYET.COM
 no shut
 ip add 10.0.2.1 255.255.254.0
ip dhcp excluded-add 10.0.2.1 10.0.2.100
ip dhcp pool FUELSYET.COM
 network 10.0.2.0 255.255.254.0
 default-router 10.0.2.1
 domain-name FUELSYET.COM
 do sh run | sec dhcp
@C2:
CONFIG T
Int e1/0
 no shut
 switchport mode access
 switchport access vlan 23
 DO SH VLAN BRIEF
@S2: 30S
config t
int e1/0
no shut
ip add dhcp
do bp
do sh ip domain


