---
layout: post
title: Hackintosh for Asus Zenbook UX 510 UW
---

There are a bunch of Asus instructions, I have even found the one for similarly named, but rather diffirent laptop UX 510 UX. It is based on KabyLake while my processor is Skylake i7-6500U.

## Few tricks, that I had to use

- For headphones to automatically detect when connected I had to inject layout 56. My audio codec is ALC256
- After sleep I had really strange bug: everything seems to be working okay, but Electron apps are freezing and it is impossible to Reboot properly
    To fix this problem I had to apply patch `change HECI to IMEI`
- In Safari I had microfreezes on some pages playing video ads and this was fixed by adding following Kext patch:
    Name: AppleIntelSKLGraphics
    Find: 83E006B9 06000000
    Replace: 31C090B9 06000000
    Comment: Turn off HDCP on HD520
    
I might update this post with new tips, stay tuned.