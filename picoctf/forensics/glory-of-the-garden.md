# Glory of the Garden

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

got a jpg of a garden. looked at it — just a normal photo. the challenge hint mentioned a hex editor which suggested something was appended to the file.

## Approach

images can have data appended after the actual image data without affecting how they render. the approach was to look at the raw content of the file for anything that shouldn't be there.

## Failed Checks

- opened the image — rendered fine, nothing hidden visually
- checked file size — slightly larger than expected for the resolution, which was a hint

<details>
<summary>Solution (spoiler)</summary>

## Solution

used `strings` to extract printable text from the binary, then grepped for the flag format:

```bash
file garden.jpg
strings garden.jpg | grep picoCTF
```

the flag appeared near the end of the strings output, appended after the image data.

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

image files can contain extra plaintext appended after the valid image data without affecting rendering. `strings` is faster than a hex editor for finding readable content.

## References

- https://github.com/kevinjycui/picoCTF-2019-writeup/blob/master/Forensics/Glory%20of%20the%20Garden/README.md
- https://picoctf2019.haydenhousen.com/forensics/glory-of-the-garden