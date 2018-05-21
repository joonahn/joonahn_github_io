---
layout: post
title: python human sorting
category: python
tags: [python, 파이썬, sort]
comments: true
---

## Human sorting 이란
사전 순 정렬이 아닌 사람이 보는 숫자 정렬 방식이다. 예를들어 컴퓨터의 사전식 정렬 방식에서는 `3` 과 `21`이 있을 때 오름차순으로 정렬하면 `3`이 `21` 다음이지만, 사람에게는 `3` 다음 `21`인 순서가 자연스럽다. 이러한 정렬 방식이 human sorting 이다.

## Human sorting sample code
```python
import re

def atoi(text):
    return int(text) if text.isdigit() else text

def natural_keys(text):
    '''
    alist.sort(key=natural_keys) sorts in human order
    http://nedbatchelder.com/blog/200712/human_sorting.html
    (See Toothy's implementation in the comments)
    '''
    return [ atoi(c) for c in re.split('(\d+)', text) ]

alist=[
    "something1",
    "something12",
    "something17",
    "something2",
    "something25",
    "something29"]

alist.sort(key=natural_keys)
print(alist)
```
결과
```python
['something1', 'something2', 'something12', 'something17', 'something25', 'something29']
```

## reference
[[stack overflow] How to correctly sort a string with a number inside?](https://stackoverflow.com/questions/5967500/how-to-correctly-sort-a-string-with-a-number-inside)