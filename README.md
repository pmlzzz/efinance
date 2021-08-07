## Introduction

[![Python Version](https://img.shields.io/badge/python-3.6+-blue.svg?style=flat)](https://pypi.python.org/pypi/efinance)
[![Pypi Package](https://img.shields.io/pypi/v/efinance.svg?maxAge=60)](https://pypi.python.org/pypi/efinance)
[![Pypi-Install](https://img.shields.io/pypi/dm/efinance.svg?maxAge=2592000&label=installs&color=%2327B1FF)](https://github.com/Micro-sheep/efinance)
[![Docs](https://readthedocs.org/projects/efinance/badge/?version=latest)](https://efinance.readthedocs.io)
[![Github Stars](https://img.shields.io/github/stars/Micro-sheep/efinance.svg?style=social&label=Star&maxAge=60)](https://github.com/Micro-sheep/efinance)

[efinance](https://github.com/Micro-sheep/efinance) 是由个人打造的用于获取股票、基金、期货数据的免费开源 Python 库，你可以使用它很方便地获取数据以便更好地服务于个人的交易系统需求。

## Installation

- 通过 `pip` 安装

```bash
pip install efinance
```

- 通过 `pip` 更新

```bash
pip install efinance --upgrade
```

- 源码安装（用于开发）

```bash
git clone https://github.com/Micro-sheep/efinance
cd efinance
pip install -e .
```

## Examples

### Stock

- 获取股票历史日 K 线数据

```python
>>> import efinance as ef
>>> # 股票代码
>>> stock_code = '600519'
>>> ef.stock.get_quote_history(stock_code)
      股票名称    股票代码          日期       开盘       收盘       最高       最低       成交量           成交额    振幅   涨跌幅    涨跌额    换手率
0     贵州茅台  600519  2001-08-27   -89.74   -89.53   -89.08   -90.07  406318.0  1.410347e+09 -1.10  0.92   0.83  56.83
1     贵州茅台  600519  2001-08-28   -89.64   -89.27   -89.24   -89.72  129647.0  4.634630e+08 -0.54  0.29   0.26  18.13
2     贵州茅台  600519  2001-08-29   -89.24   -89.36   -89.24   -89.42   53252.0  1.946890e+08 -0.20 -0.10  -0.09   7.45
3     贵州茅台  600519  2001-08-30   -89.38   -89.22   -89.14   -89.44   48013.0  1.775580e+08 -0.34  0.16   0.14   6.72
4     贵州茅台  600519  2001-08-31   -89.21   -89.24   -89.12   -89.28   23231.0  8.623100e+07 -0.18 -0.02  -0.02   3.25
...    ...     ...         ...      ...      ...      ...      ...       ...           ...   ...   ...    ...    ...
4756  贵州茅台  600519  2021-07-23  1937.82  1900.00  1937.82  1895.09   47585.0  9.057762e+09  2.20 -2.06 -40.01   0.38
4757  贵州茅台  600519  2021-07-26  1879.00  1804.11  1879.00  1780.00   98619.0  1.789436e+10  5.21 -5.05 -95.89   0.79
4758  贵州茅台  600519  2021-07-27  1803.00  1712.89  1810.00  1703.00   86577.0  1.523081e+10  5.93 -5.06 -91.22   0.69
4759  贵州茅台  600519  2021-07-28  1703.00  1768.90  1788.20  1682.12   85369.0  1.479247e+10  6.19  3.27  56.01   0.68
4760  贵州茅台  600519  2021-07-29  1810.01  1740.00  1823.00  1734.34   51035.0  9.067345e+09  5.01 -1.63 -28.90   0.41

[4761 rows x 13 columns]
```

- 获取非 A 股的股票 K 线数据（支持输入股票名称以及代码）

```python
>>> import efinance as ef
>>> # 股票代码
>>> stock_code = 'AAPL'
>>> ef.stock.get_quote_history(stock_code)
     股票名称  股票代码          日期      开盘      收盘      最高      最低          成交量           成交额    振幅   涨跌幅   涨跌额   换手率
0      苹果  AAPL  1984-09-07   -5.37   -5.37   -5.36   -5.37    2981600.0  0.000000e+00  0.00  0.00  0.00  0.02
1      苹果  AAPL  1984-09-10   -5.37   -5.37   -5.36   -5.37    2346400.0  0.000000e+00 -0.19  0.00  0.00  0.01
2      苹果  AAPL  1984-09-11   -5.36   -5.36   -5.36   -5.36    5444000.0  0.000000e+00  0.00  0.19  0.01  0.03
3      苹果  AAPL  1984-09-12   -5.36   -5.37   -5.36   -5.37    4773600.0  0.000000e+00 -0.19 -0.19 -0.01  0.03
4      苹果  AAPL  1984-09-13   -5.36   -5.36   -5.36   -5.36    7429600.0  0.000000e+00  0.00  0.19  0.01  0.04
...   ...   ...         ...     ...     ...     ...     ...          ...           ...   ...   ...   ...   ...
8739   苹果  AAPL  2021-07-22  145.94  146.80  148.19  145.81   77338156.0  1.137623e+10  1.64  0.96  1.40  0.47
8740   苹果  AAPL  2021-07-23  147.55  148.56  148.72  146.92   71447416.0  1.058233e+10  1.23  1.20  1.76  0.43
8741   苹果  AAPL  2021-07-26  148.27  148.99  149.83  147.70   72434089.0  1.080774e+10  1.43  0.29  0.43  0.44
8742   苹果  AAPL  2021-07-27  149.12  146.77  149.21  145.55  104818578.0  1.540140e+10  2.46 -1.49 -2.22  0.63
8743   苹果  AAPL  2021-07-28  144.81  144.98  146.97  142.54  118931191.0  1.723188e+10  3.02 -1.22 -1.79  0.72

[8744 rows x 13 columns]

>>> # 股票名称
>>> stock_name = '微软'
>>> ef.stock.get_quote_history(stock_name)
       股票名称  股票代码          日期      开盘      收盘      最高      最低           成交量           成交额    振幅   涨跌幅   涨跌额    换手率
0      微软  MSFT  1986-03-13  -20.74  -20.73  -20.73  -20.74  1.031789e+09  0.000000e+00  0.00  0.00  0.00  13.72
1      微软  MSFT  1986-03-14  -20.73  -20.73  -20.73  -20.73  3.081600e+08  0.000000e+00  0.00  0.00  0.00   4.10
2      微软  MSFT  1986-03-17  -20.73  -20.73  -20.73  -20.73  1.331712e+08  0.000000e+00  0.00  0.00  0.00   1.77
3      微软  MSFT  1986-03-18  -20.73  -20.73  -20.73  -20.73  6.776640e+07  0.000000e+00  0.00  0.00  0.00   0.90
4      微软  MSFT  1986-03-19  -20.73  -20.73  -20.73  -20.73  4.789440e+07  0.000000e+00  0.00  0.00  0.00   0.64
...   ...   ...         ...     ...     ...     ...     ...           ...           ...   ...   ...   ...    ...
8357   微软  MSFT  2021-07-22  283.84  286.14  286.42  283.42  2.338406e+07  6.677062e+09  1.07  1.68  4.74   0.31
8358   微软  MSFT  2021-07-23  287.37  289.67  289.99  286.50  2.276807e+07  6.578686e+09  1.22  1.23  3.53   0.30
8359   微软  MSFT  2021-07-26  289.00  289.05  289.69  286.64  2.317607e+07  6.685868e+09  1.05 -0.21 -0.62   0.31
8360   微软  MSFT  2021-07-27  289.43  286.54  289.58  282.95  3.360407e+07  9.599993e+09  2.29 -0.87 -2.51   0.45
8361   微软  MSFT  2021-07-28  288.99  286.22  290.15  283.83  3.356685e+07  9.638499e+09  2.21 -0.11 -0.32   0.45

[8362 rows x 13 columns]
```

- 获取 ETF K 线数据

```python
>>> import efinance as ef
>>> # ETF 代码（以中概互联网 ETF 为例）
>>> etf_code = '513050'
>>> ef.stock.get_quote_history(etf_code)
      股票名称    股票代码          日期     开盘     收盘     最高     最低         成交量           成交额    振幅   涨跌幅    涨跌额    换手率
0     中概互联网ETF  513050  2017-01-18  0.989  0.977  0.989  0.969    345605.0  3.381795e+07  0.00  0.00  0.000   0.26
1     中概互联网ETF  513050  2017-01-19  0.978  0.989  0.990  0.978    257716.0  2.542553e+07  1.23  1.23  0.012   0.19
2     中概互联网ETF  513050  2017-01-20  0.989  0.988  0.990  0.986     50980.0  5.043289e+06  0.40 -0.10 -0.001   0.04
3     中概互联网ETF  513050  2017-01-23  0.988  0.988  0.989  0.986     13739.0  1.356129e+06  0.30  0.00  0.000   0.01
4     中概互联网ETF  513050  2017-01-24  0.989  0.989  0.992  0.987     17937.0  1.774398e+06  0.51  0.10  0.001   0.01
...        ...     ...         ...    ...    ...    ...    ...         ...           ...   ...   ...    ...    ...
1097  中概互联网ETF  513050  2021-07-23  1.789  1.760  1.789  1.758   4427623.0  7.836530e+08  1.73 -1.51 -0.027   3.32
1098  中概互联网ETF  513050  2021-07-26  1.679  1.645  1.698  1.642  13035366.0  2.182816e+09  3.18 -6.53 -0.115   9.78
1099  中概互联网ETF  513050  2021-07-27  1.600  1.547  1.620  1.546  14269546.0  2.257610e+09  4.50 -5.96 -0.098  10.70
1100  中概互联网ETF  513050  2021-07-28  1.545  1.552  1.578  1.506  13141023.0  2.024106e+09  4.65  0.32  0.005   9.85
1101  中概互联网ETF  513050  2021-07-29  1.615  1.641  1.651  1.606  10658041.0  1.734404e+09  2.90  5.73  0.089   7.99

[1102 rows x 13 columns]
```

- 获取单只股票 5 分钟 K 线数据

```python
>>> import efinance as ef
>>> # 股票代码
>>> stock_code = '600519'
>>> # 5 分钟
>>> frequency = 5
>>> ef.stock.get_quote_history(stock_code, klt=frequency)
      股票名称    股票代码                日期       开盘       收盘       最高       最低     成交量          成交额    振幅   涨跌幅    涨跌额   换手率
0     贵州茅台  600519  2021-06-16 09:35  2172.71  2159.71  2175.71  2150.74  1885.0  411159309.0  1.15 -0.64 -14.00  0.02
1     贵州茅台  600519  2021-06-16 09:40  2156.69  2148.71  2160.48  2143.37  1238.0  268790684.0  0.79 -0.51 -11.00  0.01
2     贵州茅台  600519  2021-06-16 09:45  2149.79  2159.71  2160.69  2149.79   706.0  153631002.0  0.51  0.51  11.00  0.01
3     贵州茅台  600519  2021-06-16 09:50  2159.61  2148.87  2159.71  2148.87   586.0  127346502.0  0.50 -0.50 -10.84  0.00
4     贵州茅台  600519  2021-06-16 09:55  2148.87  2161.04  2163.71  2148.72   788.0  171491075.0  0.70  0.57  12.17  0.01
...    ...     ...               ...      ...      ...      ...      ...     ...          ...   ...   ...    ...   ...
1521  贵州茅台  600519  2021-07-29 13:50  1746.51  1746.09  1748.95  1746.01   738.0  128889575.0  0.17 -0.09  -1.49  0.01
1522  贵州茅台  600519  2021-07-29 13:55  1746.08  1742.01  1746.09  1741.96   831.0  144968679.0  0.24 -0.23  -4.08  0.01
1523  贵州茅台  600519  2021-07-29 14:00  1742.00  1739.58  1742.00  1739.58   864.0  150446840.0  0.14 -0.14  -2.43  0.01
1524  贵州茅台  600519  2021-07-29 14:05  1741.87  1740.00  1745.00  1738.88  1083.0  188427970.0  0.35  0.02   0.42  0.01
1525  贵州茅台  600519  2021-07-29 14:10  1740.00  1740.02  1740.10  1740.00    59.0   10315488.0  0.01  0.00   0.02  0.00

[1526 rows x 13 columns]
```

- 沪深市场 A 股最新状况

```python
>>> import efinance as ef
>>> ef.stock.get_realtime_quotes()
        股票代码    股票名称    涨跌幅     最新价      最高      最低    涨跌额    换手率   动态市盈率     成交量           成交额    昨日收盘          总市值          流通市值      行情ID 市场类型
0     301040     N中环  232.5   45.12    47.0   41.59  31.55  31.99   37.65   75835   326605808.0   13.57   4512000000   1069732980  0.301040   深A
1     300170    汉得信息  20.06    8.56    8.56    7.15   1.43   5.08  106.52  407546   332785856.0    7.13   7567296355   6870207362  0.300170   深A
2     300507    苏奥传感  20.02   11.51   11.51    10.5   1.92   4.23   59.52  114496   130379634.0    9.59   4935230130   3115078785  0.300507   深A
3     688316  青云科技-U   20.0   83.63   83.63    70.0  13.94   6.97  -16.13    7549    61164447.0   69.69   3969261695    906141587  1.688316   沪A
4     688682     霍莱沃   20.0  181.18  181.18  164.51   30.2   5.09  385.91    3825    67932577.0  150.98   6703660000   1361951077  1.688682   沪A
...      ...     ...    ...     ...     ...     ...    ...    ...     ...     ...           ...     ...          ...          ...       ...  ...
4589  603717    天域生态 -10.01   12.76   14.37   12.76  -1.42    1.8  177.77   43418    57832957.0   14.18   3702266022   3085320022  1.603717   沪A
4590  300118    东方日升  -12.1    17.8   19.73   17.66  -2.45   5.16   71.75  463982   850671248.0   20.25  16044206950  16010137750  0.300118   深A
4591  300511    雪榕生物 -12.18    6.92    7.33    6.86  -0.96   5.49    7.54  173540   121601875.0    7.88   3058027386   2186186828  0.300511   深A
4592  688390     固德威 -13.01  491.47   545.0  485.55 -73.53   4.15  154.62    8685   442019520.0   565.0  43249360000  10294048516  1.688390   沪A
4593  300763    锦浪科技  -15.7  244.88   278.0   244.8 -45.61   3.89  127.29   41721  1068257728.0  290.49  60627450640  26288632270  0.300763   深A

[4594 rows x 16 columns]
```

### Fund

- 获取基金历史净值信息

```python
>>> import efinance as ef
>>> ef.fund.get_quote_history('161725')
             日期    单位净值    累计净值     涨跌幅
0    2021-07-29  1.2726  2.9037   -1.52
1    2021-07-28  1.2922  2.9233    0.85
2    2021-07-27  1.2813  2.9124    -3.6
3    2021-07-26  1.3292  2.9603   -7.24
4    2021-07-23  1.4329  3.0640   -2.29
...         ...     ...     ...     ...
1502 2015-06-08  1.0380  1.0380  2.5692
1503 2015-06-05  1.0120  1.0120  1.5045
1504 2015-06-04  0.9970  0.9970      --
1505 2015-05-29  0.9950  0.9950      --
1506 2015-05-27  1.0000  1.0000      --

[1507 rows x 4 columns]
```

- 获取基金公开持仓信息

```python
>>> import efinance as ef
>>> # 获取最新公开的持仓数据
>>> ef.fund.get_inverst_position('161725')
     基金代码    股票代码  股票简称   持仓占比  较上期变化
0  161725  000858   五粮液  14.88   1.45
1  161725  600519  贵州茅台  14.16  -0.86
2  161725  600809  山西汾酒  14.03  -0.83
3  161725  000568  泸州老窖  13.02  -2.96
4  161725  002304  洋河股份  12.72   1.31
5  161725  000799   酒鬼酒   5.77   1.34
6  161725  603369   今世缘   3.46  -0.48
7  161725  000596  古井贡酒   2.81  -0.29
8  161725  600779   水井坊   2.52   2.52
9  161725  603589   口子窖   2.48  -0.38
```

- 多只基金信息

```python
>>> import efinance as ef
>>> # 获取多只基金基本信息
>>> ef.fund.get_base_info(['161725','005827'])
0  161725  招商中证白酒指数(LOF)A  2015-05-27 -6.03  1.1959   招商基金  2021-07-30     产品特色：布局白酒领域的指数基金，历史业绩优秀，外资偏爱白酒板块。
1  005827       易方达蓝筹精选混合  2018-09-05 -2.98  2.4967  易方达基金  2021-07-30  明星消费基金经理另一力作，A+H股同步布局，价值投资典范，适合长期持有。

```

### Bond

- 可转债整体行情

```python
>>> import efinance as ef
>>> ef.bond.get_realtime_quotes()
       债券代码  债券名称    涨跌幅      最新价       最高       最低     涨跌额     换手率 动态市盈率     成交量           成交额     昨日收盘         总市值        流通市值      行情ID 市场类型
0    123015  蓝盾转债  13.49  198.613    205.0    175.5  23.613  315.36     -  316062   613480512.0    175.0   199056701   199056701  0.123015   深A
1    123077  汉得转债   9.59   115.51  122.971  105.401   10.11   32.59     -  305380   358093216.0    105.4  1082332396  1082332396  0.123077   深A
2    123066  赛意转债   8.08  232.377    245.8    225.0  17.377   470.3     -  454204  1081363632.0    215.0   224423665   224423665  0.123066   深A
3    128093  百川转债   7.69  360.751    367.9    335.5  25.751  343.84     -  558874  1984944768.0    335.0   586364315   586364315  0.128093   深A
4    128082  华锋转债   7.41  158.507  163.769  147.089  10.935  103.16     -  226444   355827984.0  147.572   347931900   347931900  0.128082   深A
..      ...   ...    ...      ...      ...      ...     ...     ...   ...     ...           ...      ...         ...         ...       ...  ...
383  123087  明电转债  -4.34   151.75    169.0  150.302  -6.879  117.66     -  520370   817884784.0  158.629   671147760   671147760  0.123087   深A
384  123070  鹏辉转债  -4.63  175.001  179.799  174.471  -8.499   18.46     -  144998   257005833.0    183.5  1374730681  1374730681  0.123070   深A
385  123027  蓝晓转债  -4.67  338.413  352.825  338.015 -16.586   44.23     -   47356   162870853.0  354.999   362300558   362300558  0.123027   深A
386  113621  彤程转债  -5.03   215.61    222.5   214.41  -11.41   11.46     -   91710   200327611.0   227.02  1725268098  1725268098  1.113621   沪A
387  123047  久吾转债   -5.7    305.5   319.52  305.382  -18.47  122.41     -  193587   600277600.0   323.97   483119533   483119533  0.123047   深A

[388 rows x 16 columns]
```

- 全部可转债信息

```python
>>> import efinance as ef
>>> ef.bond.get_all_base_info()
      债券代码   债券名称    正股代码  正股名称 债券评级                 申购日期    发行规模(亿)  网上发行中签率(%)                 上市日期                 到期日期   期限(年)                                               利率说明
0   123120   隆华转债  300263  隆华科技  AA-  2021-07-30 00:00:00   7.989283         NaN                 None  2027-07-30 00:00:00       6  第一年为0.40%、第二年为0.70%、第三年为1.00%、第四年为1.60%、第五年为2....
1   110081   闻泰转债  600745  闻泰科技  AA+  2021-07-28 00:00:00  86.000000    0.044030                 None  2027-07-28 00:00:00       6  第一年0.10%、第二年0.20%、第三年0.30%、第四年1.50%、第五年1.80%、第...
2   118001   金博转债  688598  金博股份   A+  2021-07-23 00:00:00   5.999010    0.001771                 None  2027-07-23 00:00:00       6  第一年0.50%、第二年0.70%、第三年1.20%、第四年1.80%、第五年2.40%、第...
3   123119   康泰转2  300601  康泰生物   AA  2021-07-15 00:00:00  20.000000    0.014182                 None  2027-07-15 00:00:00       6  第一年为0.30%、第二年为0.50%、第三年为1.00%、第四年为1.50%、第五年为1....
4   113627   太平转债  603877   太平鸟   AA  2021-07-15 00:00:00   8.000000    0.000542                 None  2027-07-15 00:00:00       6  第一年0.30%、第二年0.50%、第三年1.00%、第四年1.50%、第五年1.80%、第...
..     ...    ...     ...   ...  ...                  ...        ...         ...                  ...                  ...     ...                                                ...
80  110227   赤化转债  600227   圣济堂  AAA  2007-10-10 00:00:00   4.500000    0.158854  2007-10-23 00:00:00  2009-05-25 00:00:00  1.6192  票面利率和付息日期:本次发行的可转债票面利率第一年为1.5%、第二年为1.8%、第三年为2....
81  126006  07深高债  600548   深高速  AAA  2007-10-09 00:00:00  15.000000    0.290304  2007-10-30 00:00:00  2013-10-09 00:00:00       6                                               None
82  110971   恒源转债  600971  恒源煤电  AAA  2007-09-24 00:00:00   4.000000    5.311774  2007-10-12 00:00:00  2009-12-21 00:00:00  2.2484  票面利率为:第一年年利率1.5%,第二年年利率1.8%,第三年年利率2.1%,第四年年利率2...
83  110567   山鹰转债  600567  山鹰国际   AA  2007-09-05 00:00:00   4.700000    0.496391  2007-09-17 00:00:00  2010-02-01 00:00:00  2.4055  票面利率和付息日期:本次发行的可转债票面利率第一年为1.4%,第二年为1.7%,第三年为2....
84  110026   中海转债  600026  中远海能  AAA  2007-07-02 00:00:00  20.000000    1.333453  2007-07-12 00:00:00  2008-03-27 00:00:00   0.737  票面利率:第一年为1.84%,第二年为2.05%,第三年为2.26%,第四年为2.47%,第...

[585 rows x 12 columns]
```

- 指定可转债 K 线数据（与 stock 模块通用）

```python
>>> import efinance as ef
>>> # 可转债代码（以 东财转3 为例）
>>> bond_code = '123111'
>>> ef.bond.get_quote_history(bond_code)
    股票名称    股票代码          日期       开盘       收盘       最高       最低      成交量           成交额    振幅    涨跌幅     涨跌额    换手率
0   东财转3  123111  2021-04-23  130.000  130.000  130.000  130.000  1836427  2.387355e+09  0.00  30.00  30.000  11.62
1   东财转3  123111  2021-04-26  130.353  130.010  133.880  125.110  8610944  1.126033e+10  6.75   0.01   0.010  54.50
2   东财转3  123111  2021-04-27  129.000  129.600  130.846  128.400  1820766  2.357472e+09  1.88  -0.32  -0.410  11.52
3   东财转3  123111  2021-04-28  129.100  130.770  131.663  128.903  1467727  1.921641e+09  2.13   0.90   1.170   9.29
4   东财转3  123111  2021-04-29  130.690  131.208  133.150  130.560  1156934  1.525974e+09  1.98   0.33   0.438   7.32
..   ...     ...         ...      ...      ...      ...      ...      ...           ...   ...    ...     ...    ...
61  东财转3  123111  2021-07-23  160.000  157.100  166.200  156.660   749059  1.201969e+09  5.98  -1.47  -2.350   4.74
62  东财转3  123111  2021-07-26  157.980  154.011  160.200  153.610   620403  9.696688e+08  4.19  -1.97  -3.089   3.93
63  东财转3  123111  2021-07-27  155.240  150.810  156.509  150.250   569574  8.709329e+08  4.06  -2.08  -3.201   3.60
64  东财转3  123111  2021-07-28  150.410  148.790  152.910  147.220   911562  1.359813e+09  3.77  -1.34  -2.020   5.77
65  东财转3  123111  2021-07-29  152.000  158.210  159.600  151.400  1061348  1.655937e+09  5.51   6.33   9.420   6.72

[66 rows x 13 columns]
```

### Futures

- 获取四大交易所期货基本信息

```python
>>> import efinance as ef
>>> ef.futures.get_futures_base_info()
       期货代码     期货名称       secid 归属交易所
0       jmm     焦煤主力     114.jmm   大商所
1    jm2109   焦煤2109  114.jm2109   大商所
2    ss2204  不锈钢2204  113.ss2204   上期所
3    jm2110   焦煤2110  114.jm2110   大商所
4    jm2111   焦煤2111  114.jm2111   大商所
..      ...      ...         ...   ...
782   i2108  铁矿石2108   114.i2108   大商所
783   i2112  铁矿石2112   114.i2112   大商所
784   i2203  铁矿石2203   114.i2203   大商所
785      im    铁矿石主力      114.im   大商所
786   i2109  铁矿石2109   114.i2109   大商所

[787 rows x 4 columns]
```

- 获取期货历史行情

```python
>>> import efinance as ef
>>> # 指定单个期货的 secid
>>> secid = '115.ZCM'
>>> ef.futures.get_quote_history(secid)
       期货名称 期货代码          日期     开盘     收盘     最高     最低     成交量           成交额    振幅   涨跌幅   涨跌额  换手率
0     动力煤主力  ZCM  2015-05-18  440.0  437.6  440.2  437.6      64  2.806300e+06  0.00  0.00   0.0  0.0
1     动力煤主力  ZCM  2015-05-19  436.0  437.0  437.6  436.0       6  2.621000e+05  0.36 -0.32  -1.4  0.0
2     动力煤主力  ZCM  2015-05-20  436.8  435.8  437.0  434.8       8  3.487500e+05  0.50 -0.23  -1.0  0.0
3     动力煤主力  ZCM  2015-05-21  438.0  443.2  446.8  437.8      37  1.631850e+06  2.06  1.65   7.2  0.0
4     动力煤主力  ZCM  2015-05-22  439.2  441.4  443.8  439.2      34  1.502500e+06  1.04  0.09   0.4  0.0
...     ...  ...         ...    ...    ...    ...    ...     ...           ...   ...   ...   ...  ...
1509  动力煤主力  ZCM  2021-07-27  897.0  892.4  915.8  888.0  109033  9.802067e+09  3.10 -0.53  -4.8  0.0
1510  动力煤主力  ZCM  2021-07-28  892.4  902.4  909.6  890.4   89853  8.086770e+09  2.14  0.38   3.4  0.0
1511  动力煤主力  ZCM  2021-07-29  902.6  918.6  919.0  900.4   83106  7.562646e+09  2.07  2.07  18.6  0.0
1512  动力煤主力  ZCM  2021-07-30  918.6  927.2  943.0  906.2  129862  1.202003e+10  4.04  1.89  17.2  0.0
1513  动力煤主力  ZCM  2021-08-02  898.0  870.0  898.0  852.4  101722  8.900675e+09  4.93 -6.01 -55.6  0.0

[1514 rows x 13 columns]

>>> secids = ['115.ZCM','115.ZC109']
>>> futures_df = ef.futures.get_quote_history(secids)
>>> type(futures_df)
<class 'dict'>
>>> futures_df.keys()
dict_keys(['115.ZC109', '115.ZCM'])
>>> futures_df['115.ZC109']
       期货名称   期货代码          日期     开盘     收盘     最高     最低     成交量           成交额    振幅   涨跌幅   涨跌额  换手率
0    动力煤109  ZC109  2020-09-09  551.2  551.2  551.2  551.2       2  1.102400e+05  0.00  0.00   0.0  0.0
1    动力煤109  ZC109  2020-09-10  548.6  545.0  549.8  545.0       6  3.289200e+05  0.87 -1.12  -6.2  0.0
2    动力煤109  ZC109  2020-09-11  545.0  544.2  548.4  543.0       7  3.815000e+05  0.99 -0.73  -4.0  0.0
3    动力煤109  ZC109  2020-09-14  546.0  550.4  550.4  546.0       7  3.843000e+05  0.81  0.99   5.4  0.0
4    动力煤109  ZC109  2020-09-15  549.0  551.2  551.6  549.0      14  7.705600e+05  0.47  0.40   2.2  0.0
..      ...    ...         ...    ...    ...    ...    ...     ...           ...   ...   ...   ...  ...
212  动力煤109  ZC109  2021-07-27  897.0  892.4  915.8  888.0  109033  9.802067e+09  3.10 -0.53  -4.8  0.0
213  动力煤109  ZC109  2021-07-28  892.4  902.4  909.6  890.4   89853  8.086770e+09  2.14  0.38   3.4  0.0
214  动力煤109  ZC109  2021-07-29  902.6  918.6  919.0  900.4   83106  7.562646e+09  2.07  2.07  18.6  0.0
215  动力煤109  ZC109  2021-07-30  918.6  927.2  943.0  906.2  129862  1.202003e+10  4.04  1.89  17.2  0.0
216  动力煤109  ZC109  2021-08-02  898.0  870.0  898.0  852.4  101722  8.900675e+09  4.93 -6.01 -55.6  0.0

[217 rows x 13 columns]
```

## Docs

在线 API 文档 [![docs](https://img.shields.io/badge/efinance-docs-blue)](https://efinance.readthedocs.io/)

如果需要本地使用，则可以使用 `pdoc` 进行文档生成
步骤如下

- 安装必要依赖

```bash
pip install pdoc efinance --upgrade
```

- 生成文档

```bash
pdoc efinance -d numpy
```

进行以上步骤之后，你将可以在弹出的浏览器界面看到文档。

同时，你也可以使用 `sphinx` 来构建 `efinance` 的文档
步骤如下

- 克隆本仓库到本地

```bash
git clone https://github.com/Micro-sheep/efinance

```

- 生成文档

```bash
cd efinance/docs
pdoc install -r requirements.txt --upgrade
sphinx-build . ./build -b html
```

经过以上步骤，你将会在 `docs/build` 下看的生成的 html 文档

## Contact

[![zhihu](https://img.shields.io/badge/知乎-blue)](https://www.zhihu.com/people/la-ge-lang-ri-96-69)
[![Github](https://img.shields.io/badge/Github-blue?style=social&logo=github)](https://github.com/Micro-sheep)
[![Email](https://img.shields.io/badge/Email-blue)](mailto:micro-sheep@outlook.com)
