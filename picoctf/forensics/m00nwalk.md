# m00nwalk

**Platform**: PicoCTF
**Category**: Forensics
**Difficulty**: Easy
**Status**: Retired

## Recon

got a wav file. played it — sounded like strange audio, not music or speech. the challenge title "m00nwalk" and the description mentioning the moon landing were strong hints.

## Approach

the moon landing used SSTV (Slow Scan Television) to transmit images as audio. the weird audio pattern matched that. the approach was to decode the audio as SSTV to recover an image containing the flag.

## Failed Checks

- listened to the audio — clearly not normal audio
- ran `strings` on the wav — nothing useful
- checked file metadata — nothing hidden there

<details>
<summary>Solution (spoiler)</summary>

## Solution

used QSSTV on Linux to decode the SSTV audio. set up a virtual audio cable to pipe the wav file into QSSTV:

```bash
# install qsstv
sudo apt install qsstv

# set up virtual sink
pactl load-module module-null-sink sink_name=virtual-cable
pavucontrol  # route qsstv input to virtual-cable

# open qsstv, then play the wav through the virtual cable
paplay -d virtual-cable message.wav
```

QSSTV decoded the audio into an image. the flag was visible in the decoded image.

**Flag**: `picoCTF{REDACTED}`

</details>

## Lessons Learned

audio files can encode images through SSTV. the challenge title and description are often the biggest clue — "moon landing" directly points to SSTV since that's how Apollo 11 transmitted images.

## References

- https://github.com/Dvd848/CTFs/blob/master/2019_picoCTF/m00nwalk.md
- https://github.com/kevinjycui/picoCTF-2019-writeup/blob/master/Forensics/m00nwalk/README.md