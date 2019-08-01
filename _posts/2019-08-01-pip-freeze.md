---
layout: post
title: How to `pip freeze` versions without bunch of dependencies
---

I don't like using `pip freeze` in my projects since it has low signal to noise ratio not showing what actual dependencies are.

But elegant solution exists! I put all my dependencies to `requirements.txt` without versions specified and then invoke:

```
pip freeze > pip_freeze.txt
grep -Fx -f requirements.txt pip_freeze.txt > nice_requirements.txt
```

### Explanation

First line saves all known requirements to file with versions.

Second line filters only manually entered requirements from that huge list, leaving only significant packages and their versions. It is done using grep with following parameters

>-F, --fixed-strings  
>        Interpret PATTERN as a list of fixed strings, separated by newlines, any of which is to be matched  
>-x, --line-regexp  
>        Select only those matches that exactly match the whole line  
>-f FILE  
>        Obtain patterns from FILE, one per line. The empty file contains zero patterns, and therefore matches nothing  

  
### Result
Effectively you get from this:
```
PyYAML
requests
result
```

to this

```
PyYAML==5.1.2
requests==2.22.0
result==0.3.0
```