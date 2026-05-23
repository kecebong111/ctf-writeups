# WhitePages

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

got a text file. opened it — appeared completely blank. but the file had a non-zero size which meant something was there.

## Approach

a "blank" file with actual bytes is a classic steganography pattern. different whitespace characters can encode binary data. the approach was to inspect the raw bytes and map them to bits.

## Failed Checks

- opened in text editor — looked empty
- ran `strings` — nothing visible
- `cat` output — blank

<details>
<summary>Solution (spoiler)</summary>

## Solution

used `xxd` to inspect the raw bytes:

```bash
xxd -g 1 whitepages.txt | head
```

found two different whitespace bytes: `0xe2 0x80 0x83` (em space) and `0x20` (regular space). mapped them to binary digits and converted to ASCII:

```python
data = open("whitepages.txt", "rb").read()
data = data.replace(b"\xe2\x80\x83", b"0")
data = data.replace(b"\x20", b"1")
bits = data.decode()
chars = [chr(int(bits[i:i+8], 2)) for i in range(0, len(bits), 8)]
print("".join(chars))
```

the output contained the flag.

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

"blank" files may contain meaningful invisible characters. different Unicode whitespace characters can encode binary data. `xxd` is the right tool to see what's actually in a file that looks empty.

## References

- https://github.com/Dvd848/CTFs/blob/master/2019_picoCTF/WhitePages.md
- https://github.com/kevinjycui/picoCTF-2019-writeup/tree/master/Forensics/WhitePages