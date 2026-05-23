# flags are stepic

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

the challenge had a website showing many country flag images. the challenge title "flags are stepic" was a direct hint — stepic is a Python steganography library for PNG images.

## Approach

one of the flag images likely had hidden data embedded using stepic. the approach was to identify the suspicious image (usually one that doesn't correspond to a real country) and decode it.

## Failed Checks

- looked at all the flag images visually — one stood out as not being a real country flag
- checked file sizes — the suspicious one (upz.png) was slightly larger than expected

<details>
<summary>Solution (spoiler)</summary>

## Solution

downloaded the suspicious flag image (upz.png) and decoded it using stepic:

```python
from PIL import Image
import stepic

img = Image.open("upz.png")
print(stepic.decode(img))
```

the decoded output was the flag.

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

challenge titles can point directly to the tool needed. "stepic" in the title = use the stepic library. file size anomalies in a set of similar files can identify the one with hidden data.

## References

- https://chrispham-cyber.github.io/posts/flags-are-stepic/
- http://mileshandelman.com/writeups/flags-are-stepic/
- https://harshit-jain52.github.io/ctf/picoCTF/Forensics/flags%20are%20stepic/