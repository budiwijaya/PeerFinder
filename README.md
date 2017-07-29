# PeeringTools

[![Build Status](https://travis-ci.org/rucarrol/PeerFinder.png)](https://travis-ci.org/rucarrol/PeerFinder)

## Intro

PeerFinder is a python script which finds common points of presence between ASNs as reported by [PeeringDB](peeringdb.com). 

The tool takes a mandatory arguments: `--asn`. There are two optional arguments to control output: `--ix-only` and `--private-only`. 

```
$ python peerfinder.py --asn 2603 13414 --ix-only
Fetching PeeringDB info for 2603
Fetching PeeringDB info for 13414
+------------------------------------+-----------------------------+-----------------------------+
|                 IX                 |        Twitter, Inc.        |           NORDUnet          |
+------------------------------------+-----------------------------+-----------------------------+
|               AMS-IX               |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 80.249.210.46      |      v4: 80.249.209.203     |
|                                    | v6: 2001:7f8:1::a501:3414:2 | v6: 2001:7f8:1::a500:2603:1 |
|                                    |      v4: 80.249.210.46      |                             |
|                                    | v6: 2001:7f8:1::a501:3414:2 |                             |
+------------------------------------+-----------------------------+-----------------------------+
|       DE-CIX Frankfurt: Main       |          AS: 13414          |           AS: 2603          |
|                                    |       v4: 80.81.194.21      |      v4: 80.81.192.241      |
|                                    |    v6: 2001:7f8::3466:0:2   |    v6: 2001:7f8::a2b:0:1    |
|                                    |       v4: 80.81.194.21      |                             |
|                                    |    v6: 2001:7f8::3466:0:2   |                             |
+------------------------------------+-----------------------------+-----------------------------+
|          Equinix Ashburn           |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 206.126.236.97     |     v4: 206.126.236.230     |
|                                    | v6: 2001:504:0:2:0:1:3414:2 |   v6: 2001:504:0:2::2603:1  |
|                                    |      v4: 206.126.236.97     |                             |
|                                    | v6: 2001:504:0:2:0:1:3414:2 |                             |
+------------------------------------+-----------------------------+-----------------------------+
|          Equinix Chicago           |          AS: 13414          |           AS: 2603          |
|                                    |     v4: 206.223.119.231     |     v4: 206.223.119.151     |
|                                    | v6: 2001:504:0:4:0:1:3414:2 |   v6: 2001:504:0:4::2603:1  |
|                                    |     v4: 206.223.119.231     |                             |
|                                    | v6: 2001:504:0:4:0:1:3414:2 |                             |
+------------------------------------+-----------------------------+-----------------------------+
|         Equinix Palo Alto          |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 198.32.176.124     |      v4: 198.32.176.208     |
|                                    |      v6: 2001:504:d::8b     |    v6: 2001:504:d::2603:1   |
|                                    |      v4: 198.32.176.124     |                             |
|                                    |      v6: 2001:504:d::8b     |                             |
+------------------------------------+-----------------------------+-----------------------------+
|                HKIX                |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 123.255.90.149     |      v4: 123.255.91.213     |
|                                    | v6: 2001:7fa:0:1::ca28:a095 |           v6: None          |
+------------------------------------+-----------------------------+-----------------------------+
|          LINX LON1: Main           |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 195.66.226.61      |      v4: 195.66.225.24      |
|                                    |    v6: 2001:7f8:4::3466:2   |    v6: 2001:7f8:4::a2b:1    |
|                                    |      v4: 195.66.226.61      |                             |
|                                    |    v6: 2001:7f8:4::3466:2   |                             |
+------------------------------------+-----------------------------+-----------------------------+
|                NOTA                |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 198.32.125.114     |      v4: 198.32.125.73      |
|                                    |    v6: 2001:478:124::1114   |    v6: 2001:478:124::1073   |
|                                    |      v4: 198.32.125.114     |                             |
|                                    |    v6: 2001:478:124::1114   |                             |
+------------------------------------+-----------------------------+-----------------------------+
|               NYIIX                |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 198.32.160.56      |      v4: 198.32.160.21      |
|                                    | v6: 2001:504:1::a501:3414:2 | v6: 2001:504:1::a500:2603:1 |
|                                    |      v4: 198.32.160.56      |                             |
|                                    | v6: 2001:504:1::a501:3414:2 |                             |
+------------------------------------+-----------------------------+-----------------------------+
| Netnod Stockholm: STH-A -- MTU1500 |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 194.68.123.229     |      v4: 194.68.123.24      |
|                                    |    v6: 2001:7f8:d:ff::229   |    v6: 2001:7f8:d:ff::24    |
+------------------------------------+-----------------------------+-----------------------------+
| Netnod Stockholm: STH-A -- MTU4470 |          AS: 13414          |           AS: 2603          |
|                                    |     v4: 195.245.240.229     |      v4: 195.245.240.24     |
|                                    |    v6: 2001:7f8:d:fc::229   |    v6: 2001:7f8:d:fc::24    |
+------------------------------------+-----------------------------+-----------------------------+
| Netnod Stockholm: STH-B -- MTU1500 |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 194.68.128.229     |      v4: 194.68.128.24      |
|                                    |    v6: 2001:7f8:d:fe::229   |    v6: 2001:7f8:d:fe::24    |
+------------------------------------+-----------------------------+-----------------------------+
| Netnod Stockholm: STH-B -- MTU4470 |          AS: 13414          |           AS: 2603          |
|                                    |      v4: 195.69.119.229     |      v4: 195.69.119.24      |
|                                    |    v6: 2001:7f8:d:fb::229   |    v6: 2001:7f8:d:fb::24    |
+------------------------------------+-----------------------------+-----------------------------+

$ python peerfinder.py --asn 2603 13414 --private-only
Fetching PeeringDB info for 2603
Fetching PeeringDB info for 13414
+----------------------------------------------------+-----------+---------+
|                      Facility                      |    City   | Country |
+----------------------------------------------------+-----------+---------+
|             Equinix Ashburn (DC1-DC11)             |  Ashburn  |    US   |
+----------------------------------------------------+-----------+---------+
|           Equinix Chicago (CH1/CH2/CH4)            |  Chicago  |    US   |
+----------------------------------------------------+-----------+---------+
|           Equinix London Docklands (LD8)           |   London  |    GB   |
+----------------------------------------------------+-----------+---------+
|              Equinix Palo Alto (SV8)               | Palo Alto |    US   |
+----------------------------------------------------+-----------+---------+
| Interxion Stockholm (STO1, STO2, STO3, STO4, STO5) | Stockholm |    SE   |
+----------------------------------------------------+-----------+---------+
|                   Verizon Miami                    |   Miami   |    US   |
+----------------------------------------------------+-----------+---------+

```


## Bugs

Probably many. PRs or bug reports very welcome. 

## Feature requests 

TODO: Make installable via pip
