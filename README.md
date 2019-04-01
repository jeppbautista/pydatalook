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
```python
import pydatalook
import pandas as pd

data = pd.read_csv("bank-additional.csv", delimiter=";")
```
### Diagnose dataframe:

```python
pydata.diagnose(data)

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
### Diagnose numeric:
```python
pydata.diagnose_numeric(data)

#                   dtype  count         mean         std       min       25%       50%       75%       max    median  zeros_cnt  negative_cnt  outliers_cnt
# age               int64   4119    40.113620   10.313362    18.000    32.000    38.000    47.000    88.000    38.000          0             0            39
# duration          int64   4119   256.788055  254.703736     0.000   103.000   181.000   317.000  3643.000   181.000          1             0           291
# campaign          int64   4119     2.537266    2.568159     1.000     1.000     2.000     3.000    35.000     2.000          0             0           235
# pdays             int64   4119   960.422190  191.922786     0.000   999.000   999.000   999.000   999.000   999.000          2             0           160
# previous          int64   4119     0.190337    0.541788     0.000     0.000     0.000     0.000     6.000     0.000       3523             0           596
# emp.var.rate    float64   4119     0.084972    1.563114    -3.400    -1.800     1.100     1.400     1.400     1.100          0          1735             0
# cons.price.idx  float64   4119    93.579704    0.579349    92.201    93.075    93.749    93.994    94.767    93.749          0             0             0
# cons.conf.idx   float64   4119   -40.499102    4.594578   -50.800   -42.700   -41.800   -36.400   -26.900   -41.800          0          4119            43
# euribor3m       float64   4119     3.621356    1.733591     0.635     1.334     4.857     4.961     5.045     4.857          0             0             0
# nr.employed     float64   4119  5166.481695   73.667904  4963.600  5099.100  5191.000  5228.100  5228.100  5191.000          0             0             0
```
### Diagnose categorical
```python
pydata.diagnose_categorical(data)

#        variable               levels  freq  count      ratio  rank
# 0           job               admin.  1012   4119  24.569070     1
# 1           job          blue-collar   884   4119  21.461520     2
# 2           job         entrepreneur   148   4119   3.593105     8
# 3           job            housemaid   110   4119   2.670551    10
# 4           job           management   324   4119   7.865987     5
# 5           job              retired   166   4119   4.030104     6
# 6           job        self-employed   159   4119   3.860160     7
# 7           job             services   393   4119   9.541151     4
# 8           job              student    82   4119   1.990774    11
# 9           job           technician   691   4119  16.775916     3
# 10          job           unemployed   111   4119   2.694829     9
# 11          job              unknown    39   4119   0.946832    12
# 12      marital             divorced   446   4119  10.827871     3
# 13      marital              married  2509   4119  60.912843     1
# 14      marital               single  1153   4119  27.992231     2
# 15      marital              unknown    11   4119   0.267055     4
# 16    education             basic.4y   429   4119  10.415149     5
# 17    education             basic.6y   228   4119   5.535324     6
# 18    education             basic.9y   574   4119  13.935421     3
# 19    education          high.school   921   4119  22.359796     2
# 20    education           illiterate     1   4119   0.024278     8
# 21    education  professional.course   535   4119  12.988589     4
# 22    education    university.degree  1264   4119  30.687060     1
# 23    education              unknown   167   4119   4.054382     7
# 24      default                   no  3315   4119  80.480699     1
# 25      default              unknown   803   4119  19.495023     2
# 26      default                  yes     1   4119   0.024278     3
# 27      housing                   no  1839   4119  44.646759     2
# 28      housing              unknown   105   4119   2.549162     3
# 29      housing                  yes  2175   4119  52.804079     1
# 30         loan                   no  3349   4119  81.306142     1
# 31         loan              unknown   105   4119   2.549162     3
# 32         loan                  yes   665   4119  16.144695     2
# 33      contact             cellular  2652   4119  64.384559     1
# 34      contact            telephone  1467   4119  35.615441     2
# 35        month                  apr   215   4119   5.219714     6
# 36        month                  aug   636   4119  15.440641     3
# 37        month                  dec    22   4119   0.534110    10
# 38        month                  jul   711   4119  17.261471     2
# 39        month                  jun   530   4119  12.867201     4
# 40        month                  mar    48   4119   1.165331     9
# 41        month                  may  1378   4119  33.454722     1
# 42        month                  nov   446   4119  10.827871     5
# 43        month                  oct    69   4119   1.675164     7
# 44        month                  sep    64   4119   1.553775     8
# 45  day_of_week                  fri   768   4119  18.645302     5
# 46  day_of_week                  mon   855   4119  20.757465     2
# 47  day_of_week                  thu   860   4119  20.878854     1
# 48  day_of_week                  tue   841   4119  20.417577     3
# 49  day_of_week                  wed   795   4119  19.300801     4
# 50     poutcome              failure   454   4119  11.022093     2
# 51     poutcome          nonexistent  3523   4119  85.530469     1
# 52     poutcome              success   142   4119   3.447439     3
# 53            y                   no  3668   4119  89.050740     1
# 54            y                  yes   451   4119  10.949260     2
```
### Diagnose outliers
```python
pydata.diagnose_outlier(data)

#                 outliers_cnt  outliers_ratio  outliers_mean  with_outliers_mean  without_outliers_mean      rate
# age                       39        0.946832      76.769231           40.113620              39.763235  1.913795
# duration                 291        7.064822     956.749141          256.788055             203.577847  3.725832
# campaign                 235        5.705268      10.612766            2.537266               2.048661  4.182756
# pdays                    160        3.884438       5.862500          960.422190             999.000000  0.006104
# previous                 596       14.469531       1.315436            0.190337               0.000000  6.911074
# emp.var.rate               0        0.000000            NaN            0.084972               0.084972       NaN
# cons.price.idx             0        0.000000            NaN           93.579704              93.579704       NaN
# cons.conf.idx             43        1.043943     -26.900000          -40.499102             -40.642566  0.664212
# euribor3m                  0        0.000000            NaN            3.621356               3.621356       NaN
# nr.employed                0        0.000000            NaN         5166.481695            5166.481695       NaN
```
### Plot outliers:
This wil generate a couple of image files.
```python
pydata.plot_outliers(data)
```
