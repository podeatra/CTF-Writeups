PCAP Analysis – picoCTF Challenge Write-up

Challenge Type: Packet Analysis
Tools Used: Wireshark, CyberChef
Flag: picoCTF{P64P_4AN4L7S1S_SU55355FUL_0F2D7DC9}

Overview:
This challenge involved analyzing a potentially poisoned .pcap (packet capture) file named trace, with no hints provided. The goal was to extract a hidden flag embedded within the network traffic.

Process:
1. Initial Observations
Opened the file in Wireshark and browsed through tcp.stream conversations.

Found early clues in:

TCP stream 1:

username: root

password: toor

This was a common default login, possibly a red herring.
Further along:

Another packet showed:

username: root

password: toorf2d7dc9}
→ This hinted at a partial flag fragment (f2d7dc9})

A malformed packet contained the message:

"flag is close"
→ Confirmed I was on the right track.

Several TCP streams included Base64 strings, one decoding to:

picoCTF

Filtering: 
In Wireshark filters used "frame contains "picoCTF" ( yes it was this easy lol )
and after that i found the packet, after decoding the hex i got "picoCTF{P64P_4AN4L7S1S_SU55355FUL_0F2D7DC9}"
