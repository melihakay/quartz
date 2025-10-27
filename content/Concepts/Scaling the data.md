---
title:
draft: false
description:
aliases:
tags:
  - statistics
date:
---
Use 
```python
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()

scaler.fit(some_series)
scaled = scaler.transform(some_series)
```

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()

scaler.fit(some_series)
scaled = scaler.transform(some_series)
```

Log transformation:
```python
from sklearn.preprocessing import PowerTransformer
scaler = PowerTransformer()

scaler.fit(some_series)
scaled = scaler.transform(some_series)