# CanYouSee

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

the challenge gave a zip file. extracted it and got a jpg. the image looked completely normal — just a photo. nothing visually suspicious.

## Approach

image forensics usually starts with the basics: file type check, strings, then metadata. the challenge hint mentioned "how to view info about the picture" which pointed directly at metadata tools.

## Failed Checks

- opened the image visually — nothing unusual
- ran `strings` on it — got some noise but nothing flag-shaped
- checked file size — seemed normal for a jpg

<details>
<summary>Solution (spoiler)</summary>

## Solution

ran exiftool on the extracted image:

```bash
unzip unknown.zip
exiftool ukn_reality.jpg
```

the output showed an `Attribution URL` field with a base64-looking string. decoded it:

```bash
echo 'BASE64_STRING_HERE' | base64 -d
```

the decoded output was the flag.

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

metadata fields can contain hidden data beyond the obvious ones. base64-looking strings in any field are always worth decoding — the `=` padding at the end is a reliable signal.

## References

- https://github.com/noamgariani11/picoCTF-2024-Writeup/blob/main/Forensics/CanYouSee.md
- https://tan-junwei.github.io/CTF-Writeups/PicoCTF/Forensics/CanYouSee