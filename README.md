# pydatalookr

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

pydatalookr is a rip-off of R's dlookr package see [here](https://github.com/choonghyunryu/dlookr). Updates will come but for now here are the features:
  - Diagnose quality of data.
  - Summarize dataframe.
  - Show and treat outliers.

## Install pydatalookr
--------------------
Coming

## Usage:
--------------------
Four main functions of pydatalook:
1. **Diagnose dataframe** 
2. **Diagnose numeric columns**
3. **Diagnose categorical columns**
4. **Diagnose outliers**
5. **Plot outliers**

### Diagnose dataframe:

```python
import pydatalook
import pandas as pd

pydata.diagnose(pd.read_csv("bank-additional.csv", delimiter=";"))
#                   dtype  missing_value_cnt  missing_value_ratio  unique_value_cnt  unique_value_ratio
# age               int64                  0                  0.0                67            1.626608
# job              object                  0                  0.0                12            0.291333
# marital          object                  0                  0.0                 4            0.097111
# education        object                  0                  0.0                 8            0.194222
# default          object                  0                  0.0                 3            0.072833
# housing          object                  0                  0.0                 3            0.072833
# loan             object                  0                  0.0                 3            0.072833
# contact          object                  0                  0.0                 2            0.048555
# month            object                  0                  0.0                10            0.242777
# day_of_week      object                  0                  0.0                 5            0.121389
# duration          int64                  0                  0.0               828           20.101966
# campaign          int64                  0                  0.0                25            0.606943
# pdays             int64                  0                  0.0                21            0.509832
# previous          int64                  0                  0.0                 7            0.169944
# poutcome         object                  0                  0.0                 3            0.072833
# emp.var.rate    float64                  0                  0.0                10            0.242777
# cons.price.idx  float64                  0                  0.0                26            0.631221
# cons.conf.idx   float64                  0                  0.0                26            0.631221
# euribor3m       float64                  0                  0.0               234            5.680991
# nr.employed     float64                  0                  0.0                11            0.267055
# y                object                  0                  0.0                 2            0.048555
```
