---
author: Nekilc
title: 量化交易指标索引
date: 2023-06-09
tags: [quantify]
---


## 真实波幅 ATR(average true range) 

真实波幅 主要应用于了解股价的震荡幅度和节奏，在窄幅整理行情中用于寻找突破时机。通常情况下股价的波动幅度会保持在一定常态下，但是如果有主力资金进出时，股价波幅往往会加剧。另外，在股价横盘整理、波幅减少到极点时，也往往会产生变盘行情。真实波幅（ATR）正是基于这种原理而设计的指标。

计算方法：

    1.TR=∣最高价-最低价∣和∣最高价-昨收∣和∣昨收-最低价∣的最大值
    2.真实波幅（ATR）=TR的N日简单移动平均
    3.参数N设置为14日

使用方法：

    如果当前价格比之前的价格高一个ATR的涨幅，买入股票
    如果之前的价格比当前价格高一个ATR的涨幅，卖出股票

## 相对强弱指数(RSI relative strength index)

相对强弱指数 是通过比较一段时期内的平均收盘涨数和平均收盘跌数来分析市场买沽盘的意向和实力，从而作出未来市场的走势。RSI在1978年6月由Wells Wider创制的一种通过特定时期内股价的变动情况计算市场买卖力量对比，来判断股票价格内部本质强弱、推测价格未来的变动方向的技术指标.

计算方法：

    RSI＝[上升平均数÷(上升平均数＋下跌平均数)]×100
    上升平均数：在某一段日子里升幅数的平均；
    下跌平均数：在同一段日子里跌幅数的平均。

使用方法：

    当RSI高于70时，股票可以被视为超买，是卖出的时候。
    当RSI低于30时，股票可以被视为超卖，是买入的时候。