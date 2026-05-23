# ctf-writeups

> writeups for retired ctf challenges. learning notes, not solution dumps.

## structure

```
.
├── _template/   # writeup template
├── htb/         # hack the box (retired only)
├── picoctf/     # picoctf
│   ├── forensics/
│   └── web-exploitation/
└── thm/         # tryhackme (retired rooms)
```

## flag policy

- retired challenges only — no active flags will be published here
- all writeup solutions are wrapped in `<details>` tags so visitors who want to attempt the challenge first can do so spoiler-free
- if you maintain a ctf platform and find content that violates your terms, open an issue and i'll archive it within 24 hours

## index

### picoctf — forensics

| challenge | year | tools |
|-----------|------|-------|
| [CanYouSee](picoctf/forensics/can-you-see.md) | 2024 | exiftool, base64 |
| [Glory of the Garden](picoctf/forensics/glory-of-the-garden.md) | 2019 | strings |
| [information](picoctf/forensics/information.md) | 2021 | exiftool, base64 |
| [m00nwalk](picoctf/forensics/m00nwalk.md) | 2019 | QSSTV, SSTV |
| [WhitePages](picoctf/forensics/whitepages.md) | 2019 | xxd, python |
| [So Meta](picoctf/forensics/so-meta.md) | 2019 | exiftool |
| [Shark on wire 1](picoctf/forensics/shark-on-wire-1.md) | 2019 | Wireshark, tshark |
| [flags are stepic](picoctf/forensics/flags-are-stepic.md) | 2019 | stepic, PIL |

### picoctf — web exploitation

| challenge | year | technique |
|-----------|------|-----------|
| [Insp3ct0r](picoctf/web-exploitation/insp3ct0r.md) | 2019 | source inspection |
| [dont-use-client-side](picoctf/web-exploitation/dont-use-client-side.md) | 2019 | JS source |
| [logon](picoctf/web-exploitation/logon.md) | 2019 | cookie manipulation |
| [where are the robots](picoctf/web-exploitation/where-are-the-robots.md) | 2019 | robots.txt |
| [picobrowser](picoctf/web-exploitation/picobrowser.md) | 2019 | User-Agent spoofing |
| [Cookies](picoctf/web-exploitation/cookies.md) | 2019 | cookie manipulation |
| [Scavenger Hunt](picoctf/web-exploitation/scavenger-hunt.md) | 2021 | source inspection |
| [GET aHEAD](picoctf/web-exploitation/get-ahead.md) | 2021 | HTTP methods |
| [Includes](picoctf/web-exploitation/includes.md) | 2022 | source inspection |
| [Inspect HTML](picoctf/web-exploitation/inspect-html.md) | 2022 | source inspection |
| [Local Authority](picoctf/web-exploitation/local-authority.md) | 2022 | JS source |
| [Search Source](picoctf/web-exploitation/search-source.md) | 2022 | source inspection |
| [Forbidden Paths](picoctf/web-exploitation/forbidden-paths.md) | 2022 | path traversal |
| [Power Cookie](picoctf/web-exploitation/power-cookie.md) | 2022 | cookie manipulation |
| [Roboto Sans](picoctf/web-exploitation/roboto-sans.md) | 2022 | robots.txt |
| [SQL Direct](picoctf/web-exploitation/sql-direct.md) | 2022 | SQL |
| [SQLiLite](picoctf/web-exploitation/sqllite.md) | 2022 | SQL injection |
| [SOAP](picoctf/web-exploitation/soap.md) | 2023 | XXE injection |
| [WebDecode](picoctf/web-exploitation/webdecode.md) | 2024 | base64 |
| [Bookmarklet](picoctf/web-exploitation/bookmarklet.md) | 2024 | JS execution |
| [IntroToBurp](picoctf/web-exploitation/introtoburp.md) | 2024 | Burp Suite |
| [Unminify](picoctf/web-exploitation/unminify.md) | 2024 | JS deobfuscation |
| [Trickster](picoctf/web-exploitation/trickster.md) | 2024 | file upload bypass |
| [Cookie Monster Secret Recipe](picoctf/web-exploitation/cookie-monster-secret-recipe.md) | 2025 | cookie manipulation |
| [SSTI1](picoctf/web-exploitation/ssti1.md) | 2025 | SSTI |

## conventions

- file naming: `{platform}/{year}/{category}/{challenge-slug}.md`
- images: ≤ 500kb each, no git lfs, prefer text over screenshots when possible
- usage: copy `_template/writeup.md`, fill in, commit