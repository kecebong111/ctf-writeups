# information

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

got a jpg called cat.jpg. the image was just a photo of a cat. nothing unusual visually.

## Approach

the challenge name "information" is a direct hint — it's about the information stored in the file, not the image itself. metadata was the first thing to check.

## Failed Checks

- looked at the image — just a cat
- ran `strings` — nothing obvious

<details>
<summary>Solution (spoiler)</summary>

## Solution

ran exiftool and noticed a suspicious `License` field:

```bash
exiftool cat.jpg
```

the License field contained a base64-encoded string. decoded it:

```bash
echo 'BASE64_STRING_HERE' | base64 -d
```

the decoded output was the flag.

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

EXIF and XMP metadata fields are one of the first things to check in image forensics. any field with a base64-looking value is worth decoding immediately.

## References

- https://7rocky.github.io/en/ctf/picoctf/forensics/information/
- https://ctftime.org/writeup/28155