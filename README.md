# QUANTAXIS 量化金融策略框架
  
QUANTAXIS量化工具箱,实现了股票和期货市场的全品种回测.通过分布式爬虫进行数据抓取,构建了响应式的数据清洗和行情推送引擎.搭建了支持多语言的开放式回测框架.并构建了交互可视化的客户端和网站.

> 0.3.8 版本将对于一体化和模块化流程进行进一步的优化


![version](https://img.shields.io/badge/Version-%200.3.8dev/RC/ARP-orange.svg)
![QAS](https://img.shields.io/badge/QUANTAXISStandardProtocol-%200.0.3-brown.svg)
![Pypi](https://img.shields.io/badge/Pypi-%200.3.8b4-blue.svg)
![Npm](https://img.shields.io/badge/Npm-%200.3.8-yellow.svg)
![author](https://img.shields.io/badge/Powered%20by-%20%20yutiansut-red.svg)
![license](https://img.shields.io/badge/License-%20MIT-brightgreen.svg)
![QQ group](https://img.shields.io/badge/QQGroup-%20563280067-yellow.svg)
![WebSite](https://img.shields.io/badge/Website-%20www.yutiansut.com-brown.svg)
![QQ](https://img.shields.io/badge/AutherQQ-%20279336410-blue.svg)


![QUANTAXIS LOGO](http://i1.piimg.com/1949/62c510db7915837a.png)
## QUANTAXIS-Stardand-Protocol
QUANTAXIS 标准化协议和未来协议

QUANTAXIS-Stardand-Protocol 版本号0.0.3

详情参见  [QUANATXISProtocol](https://github.com/yutiansut/QUANTAXIS/tree/0.3.8-dev-gamma-deal/QUANTAXISProtocol)


## 0.3.8-dev-gamma(deal)版本说明
![](http://i1.piimg.com/567571/dc3c811a5afcb4fb.png)
![](http://i4.buimg.com/567571/7d0cb26c994e90b7.png)

0.3.8-dev-gamma(deal)是在0.3.8-dev-beta(pypi)的修改版本，主要重构模拟交易部分

> 0.3.8-dev-beta使命已经完成，pip包修复，pypi版本更新到0.3.8-b0

- 当前QUANTAXIS Standard Protocol 版本号 0.0.2
- 当前QUANTAXIS Pypi 版本 0.3.8b2
- 当前QUANTAXIS-WebKit 版本 0.3.8 beta

模拟交易部分正在重构,响应式框架完成
```python
import QUANTAXIS as QA
#QA.QA_Setting.client=QA.QAUtil.QA_util_sql_mongo_setting(QA.QA_Setting.QA_util_sql_mongo_ip,QA.QA_Setting.QA_util_sql_mongo_port)
market=QA.QAMarket_core.QA_market()
bid=QA.QABid.QA_QAMarket_bid
market.market_make_deal(bid,QA.QA_Setting.client)


```
```bash
root        : INFO     deal success
root        : INFO     [from]: market  [to]:  strategy [message]: {'trade_status': 'success', 'price': '4.5', 'code': '000001.SZ', 'amount': '10', 'time': '2000-01-17', 'towards': '1'}

{
    "_id" : ObjectId("58e5389239064139208d8261"),
    "time" : ISODate("2017-04-06T02:33:54.317Z"),
    "message" : "[from]: market  [to]:  strategy [message]: {'trade_status': 'success', 'price': '4.5', 'code': '000001.SZ', 'amount': '10', 'time': '2000-01-17', 'towards': '1'}"
}
```

## 0.3.8-dev-beta(pypi)版本说明

0.3.8-dev-beta(pypi)是在dev-alpha(packages)上的bug修改版本，主要修复pip的问题

> attention: 最好有wind的包,免费/机构版都可以

> pypi version: 0.3.8-b0 / 0.3.8-b1

[为了保证最新更新，请使用git clone的方式安装]

### quantaxis
```bash
pip install quantaxis

git clone https://github.com/yutiansut/quantaxis
cd quantaxis
python setup.py install
```

### quantaxis-webkit
> 为了防止手残党打错代码,我把NPM下的quantaxis词条也注册了，因此支持npm install quantaxis  和npm install quantaxiswebkit是一个效果

``` nodejs
mkdir web && cd web
npm install quantaxiswebkit
cd node_modules/quantaxiswebkit
npm run all
```


## 使用示例
```python
import QUANTAXIS as QA

# QUANTAXIS 的API协议遵循QAS(#0.0.2)[501-0] QA_名词_动词
# 方便在写代码的时候 QA_ +tab查找你所需要的所有API
# 具体参见 QAS#0.0.2[501-0]

# get data
print(QA.QA_fetch_get_stock_day("ts","000001.SZ","2000-01-01","2017-04-01"))
print(QA.QA_fetch_get_stock_day("wind","000001.SZ","2000-01-01","2017-04-01"))
print(QA.QAWind.QA_fetch_get_stock_list('2017-04-04'))
print(QA.QAWind.QA_fetch_get_stock_indicator(name,startDate,endDate))
print(QA.QAWind.QA_fetch_get_stock_shape(name,startDate,endDate))

# save data
QA.QASU.QA_SU_save_trade_date()
QA.QASU.QA_SU_save_stock_list()
QA.QASU.QA_SU_save_stock_day(name,startDate,endDate)
#trade

# utils
print(QA.QAUtil.QA_util_date_stamp('2017-01-01'))
QA.QA_util__sql_mongo_setting
QA.QA_util_log_info()
QA.QA_util_log_debug()
QA.QA_util_log_exception()
```

初始化脚本/数据存储样式

![init](http://i4.buimg.com/567571/a3ae817d47d4529e.png)
![数据库](http://i2.muimg.com/567571/e8cb7c190b624f83.png)
```mongodb
```

## 适用场景
![适用场景](http://i2.buimg.com/567571/e2e7b31b1f9a4307.png)
考虑到这样的一个业务情景,一个机构的策略团队一般由CS+Finance组成,Finance的同学们非常擅长数据分析,策略等,但却不是很了解代码的底层架构,代码风格和标准都各有差异.而CS出身的同学们虽然对于代码和框架了如指掌,但却对枯燥空洞的金融理论一脸懵逼.而目前国内对于量化的服务支持并不能解决这个常见的场景痛点,要么是针对金融的同学的易于操作的分析系统,但对于IT而言缺少可定制化的部分;要么是针对IT的底层数据和交易接口,而对于金融的同学想从底层接口封装出来一套能用的有效率的框架简直难如登天.

QUNATAXIS致力于解决这一场景痛点,我们通过建立一个前后端分离的,基于RESTful的局域网内的标准化框架来解决这一问题.同时我们希望我们的框架是高扩展和易于接入的,以方便各个公司的各个策略团队的个性化需求(这个是最关键的,基本上每个公司都会有自己的数据,自己的交易接口,自己的特定功能目标),所以我们希望构建的是一个标准化的,高扩展性的,易于部署的脚手架,而不是一个完整的难以定制的解决方案.

QUANTAXIS的前后端完全分离,高度拆分,各个组件依赖RESTful标准的URI来进行通信,这也给了我们开放式框架的无限可能,完全可以实现Matlab,r,python,JavaScript,C,C++,rust等各个用户的和谐共处,而不是增加大家学习成本的去学习一门共用语言.同时,只要一个公网IP和服务器,你也可以超越局域网的限制,实现异地的团队的需求.




## Webkit大礼包

即将重构 #QAF03

![前后端分离](http://i1.piimg.com/567571/41fa8b9c16122bfd.png)

## 回测框架

正在重构 QAF#01
![](http://i1.piimg.com/567571/dc3c811a5afcb4fb.png)
![回测框架](http://i1.piimg.com/567571/151a21b61f4d6d63.png)