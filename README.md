# RN1_Labor2
Zweites Rechnernetze Labor

## 4.3.1
In folgenden drei Paketen geschiet der Verbindungsaufbau

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
