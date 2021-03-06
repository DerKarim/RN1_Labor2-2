# RN1_Labor2
Zweites Rechnernetze Labor

## 4.3.1
In folgenden drei Paketen geschiet der Verbindungsaufbau (connection establishment)

```
No.     Time           Source                Destination           Protocol Length
      1 0.000000       192.168.31.16         192.168.31.15         TCP      66

Frame 1: 66 bytes on wire (528 bits), 66 bytes captured (528 bits) on interface 0
Ethernet II, Src: Broadcom_0f:68:b2 (00:0a:f7:0f:68:b2), Dst: Broadcom_0f:67:02 (00:0a:f7:0f:67:02)
Internet Protocol Version 4, Src: 192.168.31.16, Dst: 192.168.31.15
Transmission Control Protocol, Src Port: 49246, Dst Port: 6777, Seq: 0, Len: 0
    Source Port: 49246
    Destination Port: 6777
    [TCP Segment Len: 0]
    Sequence number: 0    (relative sequence number)
    [Next sequence number: 0    (relative sequence number)]
    Acknowledgment number: 0
    1000 .... = Header Length: 32 bytes (8)
    Flags: 0x002 (SYN)
        .... ...0 .... = Acknowledgment: Not set
        .... .... 0... = Push: Not set
        .... .... .0.. = Reset: Not set
        .... .... ..1. = Syn: Set
        .... .... ...0 = Fin: Not set
        [TCP Flags: ··········S·]
    Window size value: 8192
    [Calculated window size: 8192]

No.     Time           Source                Destination           Protocol Length
      2 0.000109       192.168.31.15         192.168.31.16         TCP      66

Frame 2: 66 bytes on wire (528 bits), 66 bytes captured (528 bits) on interface 0
Ethernet II, Src: Broadcom_0f:67:02 (00:0a:f7:0f:67:02), Dst: Broadcom_0f:68:b2 (00:0a:f7:0f:68:b2)
Internet Protocol Version 4, Src: 192.168.31.15, Dst: 192.168.31.16
Transmission Control Protocol, Src Port: 6777, Dst Port: 49246, Seq: 0, Ack: 1, Len: 0
    Source Port: 6777
    Destination Port: 49246
    [TCP Segment Len: 0]
    Sequence number: 0    (relative sequence number)
    [Next sequence number: 0    (relative sequence number)]
    Acknowledgment number: 1    (relative ack number)
    1000 .... = Header Length: 32 bytes (8)
    Flags: 0x012 (SYN, ACK)
        .... ...1 .... = Acknowledgment: Set
        .... .... 0... = Push: Not set
        .... .... .0.. = Reset: Not set
        .... .... ..1. = Syn: Set
        .... .... ...0 = Fin: Not set
        [TCP Flags: ·······A··S·]
    Window size value: 8192
    [Calculated window size: 8192]

No.     Time           Source                Destination           Protocol Length
      3 0.000320       192.168.31.16         192.168.31.15         TCP      60

Frame 3: 60 bytes on wire (480 bits), 60 bytes captured (480 bits) on interface 0
Ethernet II, Src: Broadcom_0f:68:b2 (00:0a:f7:0f:68:b2), Dst: Broadcom_0f:67:02 (00:0a:f7:0f:67:02)
Internet Protocol Version 4, Src: 192.168.31.16, Dst: 192.168.31.15
Transmission Control Protocol, Src Port: 49246, Dst Port: 6777, Seq: 1, Ack: 1, Len: 0
    Source Port: 49246
    Destination Port: 6777
    [TCP Segment Len: 0]
    Sequence number: 1    (relative sequence number)
    [Next sequence number: 1    (relative sequence number)]
    Acknowledgment number: 1    (relative ack number)
    0101 .... = Header Length: 20 bytes (5)
    Flags: 0x010 (ACK)
        .... ...1 .... = Acknowledgment: Set
        .... .... 0... = Push: Not set
        .... .... .0.. = Reset: Not set
        .... .... ..0. = Syn: Not set
        .... .... ...0 = Fin: Not set
        [TCP Flags: ·······A····]
    Window size value: 68
    [Calculated window size: 17408]
    [Window size scaling factor: 256]
```
Man kann erkennen, dass zuerst ein SYN TCP Paket (No. 1) übermittelt wird, welches von einem SYN,ACK TCP Paket (No. 2) beantwortet wird. Dieses wiederum wird von einem ACK TCP Paket (No. 3) beantwortet.

Hier sind die Daten, welche wir über Traffic generator gesendet/empfangen haben:

```
No.     Time           Source                Destination           Protocol Length Info
      4 23.037739      192.168.31.16         192.168.31.15         TCP      154    49246 → 6777 [PSH, ACK] Seq=1 Ack=1 Win=17408 Len=100

Data (100 bytes)

0000  00 0a f7 0f 67 02 00 0a f7 0f 68 b2 08 00 45 00   ....g.....h...E.
0010  00 8c 01 4b 40 00 80 06 39 b1 c0 a8 1f 10 c0 a8   ...K@...9.......
0020  1f 0f c0 5e 1a 79 2f 6e da fe 1f 24 84 4a 50 18   ...^.y/n...$.JP.
0030  00 44 fc 75 00 00 72 65 63 68 6e 65 72 6e 65 74   .D.u..rechnernet
0040  7a 65 20 69 73 74 20 73 75 70 65 72 20 6d 69 74   ze ist super mit
0050  20 31 30 30 20 62 79 74 65 73 21 20 6d 65 73 73    100 bytes! mess
0060  61 67 65 31 41 42 43 44 45 46 47 48 49 4a 4b 4c   age1ABCDEFGHIJKL
0070  4d 4e 4f 50 51 52 53 54 55 56 57 58 59 5a 5b 5c   MNOPQRSTUVWXYZ[\
0080  5d 5e 5f 60 61 62 63 64 65 66 67 68 69 6a 6b 6c   ]^_`abcdefghijkl
0090  6d 6e 6f 70 71 72 73 74 75 76                     mnopqrstuv

No.     Time           Source                Destination           Protocol Length Info
      5 0.197097       192.168.31.15         192.168.31.16         TCP      54     6777 → 49246 [ACK] Seq=1 Ack=101 Win=17408 Len=0

No.     Time           Source                Destination           Protocol Length Info
      6 11.005912      192.168.31.16         192.168.31.15         TCP      1054   49246 → 6777 [PSH, ACK] Seq=101 Ack=1 Win=17408 Len=1000

Data (1000 bytes)

0000  00 0a f7 0f 67 02 00 0a f7 0f 68 b2 08 00 45 00   ....g.....h...E.
0010  04 10 01 4c 40 00 80 06 36 2c c0 a8 1f 10 c0 a8   ...L@...6,......
0020  1f 0f c0 5e 1a 79 2f 6e db 62 1f 24 84 4a 50 18   ...^.y/n.b.$.JP.
0030  00 44 e9 6f 00 00 72 65 63 68 6e 65 72 6e 65 74   .D.o..rechnernet
0040  7a 65 20 69 73 74 20 73 75 70 65 72 20 6d 69 74   ze ist super mit
0050  20 31 30 30 30 20 62 79 74 65 73 21 20 6d 65 73    1000 bytes! mes
0060  73 61 67 65 32 41 42 43 44 45 46 47 48 49 4a 4b   sage2ABCDEFGHIJK
....
03f0  6a 6b 6c 6d 6e 6f 70 71 72 73 74 75 76 77 78 79   jklmnopqrstuvwxy
0400  7a 41 42 43 44 45 46 47 48 49 4a 4b 4c 4d 4e 4f   zABCDEFGHIJKLMNO
0410  50 51 52 53 54 55 56 57 58 59 5a 5b 5c 5d         PQRSTUVWXYZ[\]

No.     Time           Source                Destination           Protocol Length Info
      7 0.194482       192.168.31.15         192.168.31.16         TCP      54     6777 → 49246 [ACK] Seq=1 Ack=1101 Win=16384 Len=0

No.     Time           Source                Destination           Protocol Length Info
      8 150.423555     192.168.31.16         192.168.31.15         TCP      154    49246 → 6777 [PSH, ACK] Seq=1101 Ack=1 Win=17408 Len=100

Data (100 bytes)

0000  00 0a f7 0f 67 02 00 0a f7 0f 68 b2 08 00 45 00   ....g.....h...E.
0010  00 8c 01 51 40 00 80 06 39 ab c0 a8 1f 10 c0 a8   ...Q@...9.......
0020  1f 0f c0 5e 1a 79 2f 6e df 4a 1f 24 84 4a 50 18   ...^.y/n.J.$.JP.
0030  00 44 f8 27 00 00 72 65 63 68 6e 65 72 6e 65 74   .D.'..rechnernet
0040  7a 65 20 69 73 74 20 73 75 70 65 72 20 6d 69 74   ze ist super mit
0050  20 31 30 30 20 62 79 74 65 73 21 20 6d 65 73 73    100 bytes! mess
0060  61 67 65 33 41 42 43 44 45 46 47 48 49 4a 4b 4c   age3ABCDEFGHIJKL
0070  4d 4e 4f 50 51 52 53 54 55 56 57 58 59 5a 5b 5c   MNOPQRSTUVWXYZ[\
0080  5d 5e 5f 60 61 62 63 64 65 66 67 68 69 6a 6b 6c   ]^_`abcdefghijkl
0090  6d 6e 6f 70 71 72 73 74 75 76                     mnopqrstuv

No.     Time           Source                Destination           Protocol Length Info
      9 0.211189       192.168.31.15         192.168.31.16         TCP      54     6777 → 49246 [ACK] Seq=1 Ack=1201 Win=16384 Len=0

No.     Time           Source                Destination           Protocol Length Info
     10 61.869239      192.168.31.15         192.168.31.16         TCP      154    6777 → 49246 [PSH, ACK] Seq=1 Ack=1201 Win=16384 Len=100

Data (100 bytes)

0000  00 0a f7 0f 68 b2 00 0a f7 0f 67 02 08 00 45 00   ....h.....g...E.
0010  00 8c 01 3f 40 00 80 06 00 00 c0 a8 1f 0f c0 a8   ...?@...........
0020  1f 10 1a 79 c0 5e 1f 24 84 4a 2f 6e df ae 50 18   ...y.^.$.J/n..P.
0030  00 40 bf ee 00 00 52 65 63 68 6e 65 72 6e 65 74   .@....Rechnernet
0040  7a 65 20 69 73 74 20 63 6f 6f 6c 20 3a 44 2c 20   ze ist cool :D,
0050  6d 65 73 73 61 67 65 20 34 41 42 43 44 45 46 47   message 4ABCDEFG
0060  48 49 4a 4b 4c 4d 4e 4f 50 51 52 53 54 55 56 57   HIJKLMNOPQRSTUVW
0070  58 59 5a 5b 5c 5d 5e 5f 60 61 62 63 64 65 66 67   XYZ[\]^_`abcdefg
0080  68 69 6a 6b 6c 6d 6e 6f 70 71 72 73 74 75 76 77   hijklmnopqrstuvw
0090  78 79 7a 41 42 43 44 45 46 47                     xyzABCDEFG

No.     Time           Source                Destination           Protocol Length Info
     11 0.199663       192.168.31.16         192.168.31.15         TCP      60     49246 → 6777 [ACK] Seq=1201 Ack=101 Win=17408 Len=0
```
Für jedes Paket gibt es auch hier ein ACK Paket. Man kann sehen, dass das Datensegment mit zufälligen alphanumerischen Zeichen gefüllt ist. Die in manchen enthaltene PSH Flagge bedeutet, dass das Paket direkt gesendet wird ohne auf das Füllen des Buffers zu warten.
  
  
Nun schließen wir die TCP Verbindung zwischen Server und Client. Dies sind die dabei Übertragenen Pakete:
```
No.     Time           Source                Destination           Protocol Length Info
     12 27.436960      192.168.31.15         192.168.31.16         TCP      54     6777 → 49246 [FIN, ACK] Seq=101 Ack=1201 Win=16384 Len=0

Frame 12: 54 bytes on wire (432 bits), 54 bytes captured (432 bits) on interface 0
Ethernet II, Src: Broadcom_0f:67:02 (00:0a:f7:0f:67:02), Dst: Broadcom_0f:68:b2 (00:0a:f7:0f:68:b2)
Internet Protocol Version 4, Src: 192.168.31.15, Dst: 192.168.31.16
Transmission Control Protocol, Src Port: 6777, Dst Port: 49246, Seq: 101, Ack: 1201, Len: 0
    Source Port: 6777
    Destination Port: 49246
    [TCP Segment Len: 0]
    Sequence number: 101    (relative sequence number)
    [Next sequence number: 101    (relative sequence number)]
    Acknowledgment number: 1201    (relative ack number)
    0101 .... = Header Length: 20 bytes (5)
    Flags: 0x011 (FIN, ACK)
        .... ...1 .... = Acknowledgment: Set
        .... .... 0... = Push: Not set
        .... .... .0.. = Reset: Not set
        .... .... ..0. = Syn: Not set
        .... .... ...1 = Fin: Set
        [TCP Flags: ·······A···F]
    Window size value: 64
    [Calculated window size: 16384]
    [Window size scaling factor: 256]

No.     Time           Source                Destination           Protocol Length Info
     13 0.000378       192.168.31.16         192.168.31.15         TCP      60     49246 → 6777 [ACK] Seq=1201 Ack=102 Win=17408 Len=0

Frame 13: 60 bytes on wire (480 bits), 60 bytes captured (480 bits) on interface 0
Ethernet II, Src: Broadcom_0f:68:b2 (00:0a:f7:0f:68:b2), Dst: Broadcom_0f:67:02 (00:0a:f7:0f:67:02)
Internet Protocol Version 4, Src: 192.168.31.16, Dst: 192.168.31.15
Transmission Control Protocol, Src Port: 49246, Dst Port: 6777, Seq: 1201, Ack: 102, Len: 0
    Source Port: 49246
    Destination Port: 6777
    [TCP Segment Len: 0]
    Sequence number: 1201    (relative sequence number)
    [Next sequence number: 1201    (relative sequence number)]
    Acknowledgment number: 102    (relative ack number)
    0101 .... = Header Length: 20 bytes (5)
    Flags: 0x010 (ACK)
        .... ...1 .... = Acknowledgment: Set
        .... .... 0... = Push: Not set
        .... .... .0.. = Reset: Not set
        .... .... ..0. = Syn: Not set
        .... .... ...0 = Fin: Not set
        [TCP Flags: ·······A····]
    Window size value: 68
    [Calculated window size: 17408]
    [Window size scaling factor: 256]

No.     Time           Source                Destination           Protocol Length Info
     14 0.013742       192.168.31.16         192.168.31.15         TCP      60     49246 → 6777 [FIN, ACK] Seq=1201 Ack=102 Win=17408 Len=0

Frame 14: 60 bytes on wire (480 bits), 60 bytes captured (480 bits) on interface 0
Ethernet II, Src: Broadcom_0f:68:b2 (00:0a:f7:0f:68:b2), Dst: Broadcom_0f:67:02 (00:0a:f7:0f:67:02)
Internet Protocol Version 4, Src: 192.168.31.16, Dst: 192.168.31.15
Transmission Control Protocol, Src Port: 49246, Dst Port: 6777, Seq: 1201, Ack: 102, Len: 0
    Source Port: 49246
    Destination Port: 6777
    [TCP Segment Len: 0]
    Sequence number: 1201    (relative sequence number)
    [Next sequence number: 1201    (relative sequence number)]
    Acknowledgment number: 102    (relative ack number)
    0101 .... = Header Length: 20 bytes (5)
    Flags: 0x011 (FIN, ACK)
        .... ...1 .... = Acknowledgment: Set
        .... .... 0... = Push: Not set
        .... .... .0.. = Reset: Not set
        .... .... ..0. = Syn: Not set
        .... .... ...1 = Fin: Set
        [TCP Flags: ·······A···F]
    Window size value: 68
    [Calculated window size: 17408]
    [Window size scaling factor: 256]

No.     Time           Source                Destination           Protocol Length Info
     15 0.000032       192.168.31.15         192.168.31.16         TCP      54     6777 → 49246 [ACK] Seq=102 Ack=1202 Win=16384 Len=0

Frame 15: 54 bytes on wire (432 bits), 54 bytes captured (432 bits) on interface 0
Ethernet II, Src: Broadcom_0f:67:02 (00:0a:f7:0f:67:02), Dst: Broadcom_0f:68:b2 (00:0a:f7:0f:68:b2)
Internet Protocol Version 4, Src: 192.168.31.15, Dst: 192.168.31.16
Transmission Control Protocol, Src Port: 6777, Dst Port: 49246, Seq: 102, Ack: 1202, Len: 0
    Source Port: 6777
    Destination Port: 49246
    [TCP Segment Len: 0]
    Sequence number: 102    (relative sequence number)
    [Next sequence number: 102    (relative sequence number)]
    Acknowledgment number: 1202    (relative ack number)
    0101 .... = Header Length: 20 bytes (5)
    Flags: 0x010 (ACK)
        .... ...1 .... = Acknowledgment: Set
        .... .... 0... = Push: Not set
        .... .... .0.. = Reset: Not set
        .... .... ..0. = Syn: Not set
        .... .... ...0 = Fin: Not set
        [TCP Flags: ·······A····]
    Window size value: 64
    [Calculated window size: 16384]
    [Window size scaling factor: 256]
```
Zum ersten mal sehen wir ein gesetztes FIN Flag, welches dem TCP Partner mitteilt, dass der Sender die Verbindung ordnungsgemäß schliesen will. Es folgt ein ACK und ein FIN ACK vom Partner. Der Sender bestätig den Erhalt dieses Pakets mit einem letzten ACK Pakets.

## 4.3.2

Bei dieser Aufgabe werden wir unser TCP Empfangsfenster etwas auslasten. Dies erfolgt durch verschicken von 100 Datenpaketen mit einer Größe von 1000 bytes. Das besondere hierbei ist, dass wir die Datenpakete erst nach einer Minute receiven werden.

```
15	84.609223	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=8001 Win=17408 Len=0	0.000024
18	84.611739	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=10461 Win=14848 Len=0	0.000032
21	84.613248	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=12001 Win=13312 Len=0	0.000027
24	84.615807	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=14461 Win=11008 Len=0	0.000024
27	84.617315	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=16001 Win=9472 Len=0	0.000025
30	84.619225	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=18001 Win=7424 Len=0	0.000024
33	84.621178	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=20001 Win=5376 Len=0	0.000023
36	84.623687	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=22461 Win=2816 Len=0	0.000029
39	84.625204	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=24001 Win=1280 Len=0	0.000024
41	84.818497	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=25001 Win=512 Len=0	0.192208
43	89.841623	192.168.31.15	192.168.31.16	TCP	54	[TCP ZeroWindow] 6777 → 49479 [ACK] Seq=1 Ack=25513 Win=0 Len=0	0.211630
45	90.450014	192.168.31.15	192.168.31.16	TCP	54	[TCP ZeroWindow] [TCP ACKed unseen segment] 6777 → 49479 [ACK] Seq=1 Ack=25514 Win=0 Len=0	0.210406
47	91.666785	192.168.31.15	192.168.31.16	TCP	54	[TCP ZeroWindow] [TCP ACKed unseen segment] 6777 → 49479 [ACK] Seq=1 Ack=25515 Win=0 Len=0	0.217158
49	94.115933	192.168.31.15	192.168.31.16	TCP	54	[TCP ZeroWindow] [TCP ACKed unseen segment] 6777 → 49479 [ACK] Seq=1 Ack=25516 Win=0 Len=0	0.206250
51	99.045427	192.168.31.15	192.168.31.16	TCP	54	[TCP ZeroWindow] [TCP ACKed unseen segment] 6777 → 49479 [ACK] Seq=1 Ack=25517 Win=0 Len=0	0.205547
53	108.701627	192.168.31.15	192.168.31.16	TCP	54	[TCP ZeroWindow] [TCP ACKed unseen segment] 6777 → 49479 [ACK] Seq=1 Ack=25518 Win=0 Len=0	0.211569
55	127.795656	192.168.31.15	192.168.31.16	TCP	54	[TCP ZeroWindow] [TCP ACKed unseen segment] 6777 → 49479 [ACK] Seq=1 Ack=25519 Win=0 Len=0	0.215101
56	144.985757	192.168.31.15	192.168.31.16	TCP	54	[TCP Window Update] 6777 → 49479 [ACK] Seq=1 Ack=25519 Win=4352 Len=0	17.190101
59	144.988524	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=28439 Win=1536 Len=0	0.000023
61	145.018830	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=29899 Win=13056 Len=0	0.028823
64	145.021560	192.168.31.15	192.168.31.16	TCP	54	6777 → 49479 [ACK] Seq=1 Ack=32819 Win=9984 Len=0	0.000015
```

## 4.3.4

Die Verbindung kann hier nicht aufgebaut werden, bevor der Server auf Listen schaltet. Wir bekommen eine RST/ACK Antwort zurück. Der Client denkt, dass unsere Nachrichten verloren gegangen sind. Deshalb versucht er die Nachrichten erneut zu senden. Da die Verbindung nicht vorhanden ist, geht sie verloren und es werden Retransmissions durchgeführt. Diesmal wird aber keine Reset Flag gesetzt, da der Server nicht erreichbar ist.

```
1	0.000000	192.168.31.16	192.168.31.15	TCP	66	49695 → 6777 [SYN] Seq=0 Win=8192 Len=0 MSS=1460 WS=256 SACK_PERM=1	0.000000
2	0.000305	192.168.31.15	192.168.31.16	TCP	54	6777 → 49695 [RST, ACK] Seq=1 Ack=1 Win=0 Len=0	0.000305
3	0.509040	192.168.31.16	192.168.31.15	TCP	66	[TCP Retransmission] 49695 → 6777 [SYN] Seq=0 Win=8192 Len=0 MSS=1460 WS=256 SACK_PERM=1	0.508735
4	0.509093	192.168.31.15	192.168.31.16	TCP	54	6777 → 49695 [RST, ACK] Seq=1 Ack=1 Win=0 Len=0	0.000053
5	1.009033	192.168.31.16	192.168.31.15	TCP	62	[TCP Retransmission] 49695 → 6777 [SYN] Seq=0 Win=8192 Len=0 MSS=1460 SACK_PERM=1	0.499940
6	1.009087	192.168.31.15	192.168.31.16	TCP	54	6777 → 49695 [RST, ACK] Seq=1 Ack=1 Win=0 Len=0	0.000054
7	22.294197	192.168.31.16	192.168.31.15	TCP	66	49696 → 6777 [SYN] Seq=0 Win=8192 Len=0 MSS=1460 WS=256 SACK_PERM=1	21.285110
8	25.293650	192.168.31.16	192.168.31.15	TCP	66	[TCP Retransmission] 49696 → 6777 [SYN] Seq=0 Win=8192 Len=0 MSS=1460 WS=256 SACK_PERM=1	2.999453
9	31.293748	192.168.31.16	192.168.31.15	TCP	62	[TCP Retransmission] 49696 → 6777 [SYN] Seq=0 Win=8192 Len=0 MSS=1460 SACK_PERM=1	6.000098
```


