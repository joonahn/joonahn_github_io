---
layout: post
title: pandas 기초
category: pandas
tags: [python, 파이썬, pandas]
comments: true
---

## csv 파일 불러오기
단일 csv 파일 불러오기
```python
import pandas as pd

df = pd.read_csv(file)
```
여러 개의 csv 파일을 한꺼번에 불러오기 (파일 형식은 같은 경우)
```python
import pandas as pd

file_list = ["file1.csv", "file2.csv"]
list_ = []

for f in file_list:
    df = pd.read_csv(f)
    list_.append(df)

df = pd.concat(list_)
```

## 특정 column의 데이터를 list로 변환
```python
>>> df["TARGET_COLUMN_NAME"].values.tolist()
['0', '1', '2', ...]
```

## 특정 column 만 보기
```python
>>> df[["TARGET_COLUMN_NAME"]]
<pandas.core.frame.DataFrame>
```

## 특정 row만 filter
row의 `TARGET_COLUMN_NAME` 컬럼 값이 target_value와 같은 경우만 filter
```python
>>> df[df["TARGET_COLUMN_NAME" == target_value]]
<pandas.core.frame.DataFrame>
```

## row 정렬
row의 `TARGET_COLUMN_NAME` 컬럼 값으로 row 정렬. 정렬로 row의 순서가 바뀌어도 index는 바뀌지 않는다.
```python
>>> df.sort_values(["TARGET_COLUMN_NAME"], ascending=True)
<pandas.core.frame.DataFrame>
```

## 특정 index의 row만 뽑기
```python
>>> df.iloc[[1,2,3]]
<pandas.core.frame.DataFrame>
```

## pandas row index 초기화
```python
>>> df.reset_index()
<pandas.core.frame.DataFrame>
```

## 데이터 분석
```python
>>> df.describe()
<pandas.core.frame.DataFrame>
```