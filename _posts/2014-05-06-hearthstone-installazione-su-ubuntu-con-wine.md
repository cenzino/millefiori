---
layout: post
title: "Hearthstone: installazione su Ubuntu con Wine"
description: ""
category: 
tags: [ubuntu]
---

```console
$ sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```console
$ sudo apt-get update
```

```console
$ sudo apt-get install wine1.7 winetricks
```


**dbghelp**

Run winecfg
In the libraries tab, type dbghelp into the New override for library box.
Click Add, then Yes when it asks.
Click on dbghelp in the Existing_overrides list.
Click Edit.
Set to Disabled.
Click Ok. Then Ok.

**msvcp100**

Run winecfg
In the libraries tab, type msvcp100 into the New override for library box.
Click Add, then Yes when it asks.
Click on msvcp100 in the Existing_overrides list.
Click Edit.
Set to native,embedded.
Click Ok. Then Ok.

You also need to run the following command in a terminal and wait for it to complete:

winetricks wininet
