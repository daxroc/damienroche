---
author: "Damien Roche"
date: 2013-10-21
linktitle: Bash Clear & Present characters
title: Viewing hidden characters in a file
highlight: true
url: /blog/misc/hidden_characters.html
---

Debugging unwanted characters being appended to the output of a recent bash script led me to this gem, how to show raw unescaped terminal output using sed

```
command | sed -n ‘l’
sed -n ‘l’ file.txt
```

Turns out my problem was with a ‘clear’ command appending the following “33[H33[2J$” to the output which was later being parsed by another script.
