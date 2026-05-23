# So Meta

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

got a png image. the challenge name "So Meta" is a direct hint — it's about metadata.

## Approach

ran exiftool immediately given the challenge name. no need to look further.

## Failed Checks

- opened the image — nothing unusual visually

<details>
<summary>Solution (spoiler)</summary>

## Solution

```bash
exiftool pico_img.png
```

the flag appeared directly in one of the metadata fields, commonly the `Artist` field.

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

challenge titles often directly hint at the intended technique. "So Meta" = metadata. when the title is this obvious, start there and don't overthink it.

## References

- https://github.com/kevinjycui/picoCTF-2019-writeup/tree/master/Forensics/So%20Meta
- https://github.com/SrivathsanNayak/ethical-hacking-notes/blob/main/picoCTF/picoGym/README.md#so-meta