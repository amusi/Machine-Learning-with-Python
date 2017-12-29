# Machine-Learning-with-Python
Machine-Learning-with-Python follow sentdex



# 1 Intro

# 2 Regression Intro

Install necessary libs/modules

```shell
pip install sklearn
pip install quandl
```

create Regression_Intro.py

```python
import pandas as pd
import quandl

df = quandl.get('WIKI/GOOGL')
# print(df.head())

df = df[['Adj. Open', 'Adj. High', 'Adj. Low', 'Adj. Close', 'Adj. Volume', ]]
df['HL_PCT'] = (df['Adj. High'] - df['Adj. Close']) / df['Adj. Close'] * 100.0
df['PCT_change'] = (df['Adj. Close'] - df['Adj. Open']) / df['Adj. Open'] * 100.0

df = df[['Adj. Close', 'HL_PCT', 'PCT_change', 'Adj. Volume']]
print(df.head())
```

# 3 Regression Features and Labels

```python
import pandas as pd
import quandl
import math

df = quandl.get('WIKI/GOOGL')
# print(df.head())

df = df[['Adj. Open', 'Adj. High', 'Adj. Low', 'Adj. Close', 'Adj. Volume', ]]
df['HL_PCT'] = (df['Adj. High'] - df['Adj. Close']) / df['Adj. Close'] * 100.0
df['PCT_change'] = (df['Adj. Close'] - df['Adj. Open']) / df['Adj. Open'] * 100.0

df = df[['Adj. Close', 'HL_PCT', 'PCT_change', 'Adj. Volume']]

forecast_col = 'Adj. Close'
df.fillna(-9999, inplace=True)

forecast_out = int(math.ceil(0.1*len(df)))

df['label'] = df[forecast_col].shift(-forecast_out)
df.dropna(inplace=True)
print(df.head())
#print(df.tail())
```

