---
layout: post
title:  "Linux的find命令"
date:   2019-04-26 12:00:00
categories: Linux
tags: [linuxcommand]
---

## find,grep,sed命令以及xargs

### find
find命令的默认action是-print，`find . -type f | grep x`就相当于`find . -type f -print | grep x`，即在文件名里查找x字符。<!-- more -->

如果要在查找出的文件里边查找字符，使用find命令的自定义操作-exec或xargs
```
#-exec
find . -type f -exec grep x '{}' ';'
#-xargs
find . -type f | xargs grep x
```

### find + sed
查找所有文件，并替换文件里的字符，将所有old替换为new，
```
find . -type f | xargs sed -i 's/old/new/g'
```

### find + grep + sed
查找含有特定字符的文件，并对这些文件进行字符替换，如
```
find . -name '*.java' -type f | xargs grep -l bb | xargs sed -i 's/bb/aa/g'
```