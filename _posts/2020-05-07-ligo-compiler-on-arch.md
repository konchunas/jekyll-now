---
layout: post
title: Installing binary LIGO compiler on Any Linux
---

I don't quite understand this new trend of wrapping everything up into containers. Especially when we are talking about software not really requiring that much of an environemnt. And especially on Linux where `docker` should be run from superuser at all times.

LIGO compiler is distributed either by docker image or binary .deb package, not really available to be installed on non-Debian systems. But here is a simple trick. Just unpack .deb archive contents using any archiver. Inside there is `data.tar.xz` file. Unpack it as well. There is your ligo compiler in `bin` folder. It may not launch unless you have some dependencies installed, so lets install them by running:
``` bash
sudo pacman -Syu libev
```

Now your `ligo` binary runs perfectly well and you are ready to compile your smart contracts.