---
title:
draft: false
description:
aliases:
tags:
  - statistics
  - pandas
date:
---
Similar to [[One-hat encoding]].

>[!info] It maps N features to N-1 variables my setting first one to all-zero.

>[!tip] Pandas
>```python
>encoded = pd.get_dummies(
>	df, columns=["Col1"], 
>	drop_first=True, prefix="C"
>)
>```

Eliminates duplicate columns. Take gender as example.