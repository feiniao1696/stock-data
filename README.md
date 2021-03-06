﻿
## 五分钟/一分钟数据下载

原始数据可以通过搜索 ghancn 免费下载 2009 年之前的数据。2009 年之后的需要购买。目前的免费数据质量不高，里面有不少错误。有两种样式的数据，一种是五分钟数据，一种是一分钟数据。这里使用的是五分钟数据进行分析。

### 数据格式

文本格式内容是：时间，开盘，最高，最低，收盘 ，成交量，成交额

### 数据清洗

* 数据异常
    * 有些交易数据有 0 项，丢弃这些数据
    * 5 分钟数据涨跌幅异常，如
        * SZ161607.csv: 2008/11/19,15:00,67315720.000,67315720.000,67315720.000,67315720.000,5939115008.00,602104324547466120000000000000000.00
        * SZ000564.csv: 2001/11/30,09:35,8.50,503.38,8.50,503.38,1139.00,1218485.75
        * SZ131809.csv: 2002/05/13,13:10,100.450,100.450,100.450,100.450,0.00,0.00
    * 日涨跌幅异常，如
        * SH900956.csv: 1458  2006/04/19  0.226   0.231   0.232   3695.00     84236       0.227
        * SH900956.csv: 1459  2006/04/20  99.710  99.740  99.750  133188.00   132826112   99.730
        * SZ000564.csv: 2092  2008/12/31  3.15    3.25    3.28    17421.04    5621867.50  3.18
        * SZ000564.csv: 2093  2000/01/04  7.35    7.35    7.85    15022.49    11510977.00 7.77
* 计算涨跌幅
* 除权标记
    * 借壳上市的股票，重新交易的首日，上涨幅度可能超过 10%
      如 SZ000728 2007/03/26 2007/10/30，SH600691 2007-01-18 2007-05-28
    * 10 派 10 分红时，未除权数据，股价可能下跌超过 10%
* 黑名单，对一些数据质量极差的，就不做容错处理，而是直接放在黑名单里
    * SZ131809: 数据质量极差，基本都超出了涨跌停限制，严重影响通过波动幅度自动选股策略。放进黑名单。

## 雅虎数据下载

雅虎财经网站提供股票日历史数据下载接口。

直接在浏览器地址中数据网址即可 `http://table.finance.yahoo.com/table.csv?s=股票代码`。上证股票是股票代码后面加上.ss，深证股票是股票代码后面加上.sz。例如查询中国石油的历史数据，直接在浏览器中输入：http://table.finance.yahoo.com/table.csv?s=601857.ss

深市数据链接：http://table.finance.yahoo.com/table.csv?s=000001.sz
上市数据链接：http://table.finance.yahoo.com/table.csv?s=600000.ss

另外，上证综指代码：000001.ss，深证成指代码：399001.SZ，沪深300代码：000300.ss

### 字段格式

Date Open High Low Close Volume Adj Close
分别是：日期、开盘价、最高价、最低价、收盘价、成交量、复权收盘价 

### 获取指定时间范围的数据

【例子】 取 2012年1月1日 至 2012年4月19日的数据
http://table.finance.yahoo.com/table.csv?a=0&b=1&c=2012&d=3&e=19&f=2012&s=600000.ss

## 机器学习特征选择

* 上一交易日价格
* 上一交易日成交量
* 最近 5 日平均价格
* 最近 5 日平均成交量
* 最近 10 日平均价格
* 最近 10 日平均成交量
* 最近 30 日平均价格
* 最近 30 日平均成交量
* 最近 60 日平均价格
* 最近 60 日平均成交量
* 上证上一交易日点位
* 上证上一交易日成交量
* 上证最近 5 日平均点位
* 上证最近 5 日平均成交量
* 上证最近 10 日平均点位
* 上证最近 10 日平均成交量
* 上证最近 30 日平均点位
* 上证最近 30 日平均成交量
* 上证最近 60 日平均点位
* 上证最近 60 日平均成交量
* 深证上一交易日点位
* 深证上一交易日成交量
* 深证最近 5 日平均点位
* 深证最近 5 日平均成交量
* 深证最近 10 日平均点位
* 深证最近 10 日平均成交量
* 深证最近 30 日平均点位
* 深证最近 30 日平均成交量
* 深证最近 60 日平均点位
* 深证最近 60 日平均成交量
