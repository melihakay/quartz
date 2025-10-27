---
title: 
draft: false
description: 
aliases: 
tags: 
date:
---
Used for binning the numerical values.

```python
df["Binned"] = pd.cut(
	df["col"],
	bins=[-np.inf, 0, 2, np.inf],
	labels=[1,2,3]
)
```
""