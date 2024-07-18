---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
# weight: 1
tags: ["first"]
author: "TomasCostaK"

showToc: false
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "This is a post"
disableHLJS: true # to disable highlightjs
disableShare: true
disableHLJS: true
hideSummary: false

cover:
  image: "covers/cover1.png"
  relative: true
    
editPost:
    URL: "https://github.com/TomasCostaK/portfolio/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
This is a post, and the following is Python code:

```python
print("hello world")
```