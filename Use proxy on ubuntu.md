---
title: Use proxy on ubuntu
date: 2021-11-21 16:37:36
tags:
---

# Use proxy on ubuntu

### install proxychains4

```shell
sudo apt install proxychains4
```

### config

```shell
sudo emacs /etc/proxychains4.conf
# add proxy server in the last line
# sock5 192.168.192.1 1080
```

### Test use proxy

```shell
proxychains wget google.com
```

