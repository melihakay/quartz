---
title:
draft: false
description:
aliases:
tags:
  - pandas
date:
---
# List-wise Deletion

Use to drop NA's:

```python
df.dropna(how="any") # to drop all rows with at least one missing value.
# You can pass axis=1 to drop column.
df.dropna(subset=["Col1"]) # to drop all rows with missing value on Col1
```

Use to fill NA's:

```python
df["Col"].fillna(
	value="None", inplace=True
)
```

Mask `notnull` by `df["ValueGiven"] = df["Col1"].notnull()`.

# Replacing

## Numerical Values

One may use mean or median, but it can mess up the variance and covariance.