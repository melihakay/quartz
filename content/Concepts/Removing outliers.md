---
title:
draft: false
description:
aliases:
tags:
  - statistics
date:
---
```python
q_cut = df["col_name"].quantile(0.95)
trimmed = df[df["col_name"] < q_cut]
```

or 

```python
std, mean = df["col_name"].std(), df["col_name"].mean()
lower = mean - 3*std
upper = mean + 3*std
trimmed = df[
	df["col_name"] > lower &\
	df["col_name"] < upper
]
```

