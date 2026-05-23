# Shark on wire 1

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

got a pcap file. opened it in Wireshark — lots of network traffic. the challenge name references Wireshark (the shark) and network capture.

## Approach

pcap forensics usually means reconstructing conversations. the flag was likely hidden in one of the UDP streams. the approach was to follow UDP streams until finding the flag.

## Failed Checks

- filtered for TCP streams first — nothing useful
- looked at HTTP traffic — nothing there
- checked DNS queries — nothing flag-shaped

<details>
<summary>Solution (spoiler)</summary>

## Solution

filtered for UDP traffic in Wireshark, then followed individual streams:

```
Filter: udp
Right-click packet → Follow → UDP Stream
```

tried streams one by one. stream 6 contained the flag as readable text.

CLI alternative:

```bash
tshark -r capture.pcap -Y "udp.stream eq 6" \
  -T fields -e data.text -o data.show_as_text:TRUE
```

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

pcap forensics often means reconstructing conversations, not reading packets individually. following streams (UDP or TCP) is faster than inspecting raw packets. try multiple stream numbers if the first few are empty.

## References

- https://github.com/Dvd848/CTFs/blob/master/2019_picoCTF/shark_on_wire_1.md
- https://github.com/HHousen/PicoCTF-2019/blob/master/Forensics/shark%20on%20wire%201/README.md