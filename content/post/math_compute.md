---
title: "Simple math notes"
date: 2019-04-11 
weight: 70
keywords: ["python","compute"]
description: "simple math notes"
tags: [ "math"]
categories: ["Projects_SMU"]
author: "KennaNing"
---

# np.mean()
```
matrix=[[1,2,3],[2,3,4],[3,4,5],[4,5,6]]
np.mean(matrix) -> 3.5                   对所有元素求均值
np.mean(matrix,0) -> [2.5,3.5,4.5]       对各列求均值,压缩行
np.mean(matrix,1) -> [[2],[3],[4],[5]]   对各行求均值，压缩列
```
