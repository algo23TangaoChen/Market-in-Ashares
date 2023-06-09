# 石川《因子投资》第三章A股市场因子复刻

## 目录

- [背景](#背景)
- [数据选择](#数据选择)
- [时序回归](#时序回归)
- [计算组合月均收益率和beta的秩相关系数检验单调性](#计算组合月均收益率和beta的秩相关系数检验单调性)
- [项目负责人](#项目负责人)

## 背景
这是本人第一次尝试使用python复刻金融市场研究相关的项目，主要目的在于练习pandas数据处理和金融统计的基本方法，由于经验不足，没有很好地利用pandas的很多属性和方法，代码的效率和优雅性比较低。

## 数据选择
- 样本空间：20200101-20230130内全体A股，剔除ST、*ST和上市时间不足样本时间序列1/3的股票
- 数据来源：A股量价数据来自qstock数据库
- 本例中无风险利率参考锐思数据的计算方式，2006年之后用上海银行三个月同业拆借利率作为无风险利率
而了解无风险利率最简便快捷的方式，就是看当前的同业拆借利率。在普通的拆借交易中，大银行基本上不会有违约的风险，而且同业拆借市场资金量大，流动性好，随时都能够有交易，不会出现有价无市的情况。所以（除开国债之外），同业拆借大概是最接近无风险的交易，而拆借的利率也就是最方便的模拟无风险利率的一个指标。有了这个指标，很多金融产品才能够定价，顺利的完成交易。
作者：Luo Patrick 链接：https://www.zhihu.com/question/20078836/answer/13902696 来源：知乎 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。


## 时序回归
参考石川《因子投资》原文，采用样本期内资产收益率与同期的市场收益进行时序回归，并且选择异方差稳健标准误（CAPM）模型，测算每个样本在训练期内的beta


## 计算组合月均收益率和beta的秩相关系数检验单调性
- 用Pearson相关系数和Spearman相关系数检验beta和收益率的相关性

- 等权重时，组合收益与beta并没有表现出显著的单调性

- 用斯皮尔曼秩相关系数检验单调性的好处：作为一种非参数估计，不要求已知序列的分布，因此用途更广泛

- 观察组合可以发现，存在负beta但是高收益率的组合，与CAPM和Black CAPM都不同。原因可能是样本剔除不干净，留下了异常值

- 参考因子投资原文，CAPM同样被A股数据拒绝。原文也存在低beta异象。前者的解释应该是在CAPM模型中加入风格因子，后者作为异象需要进一步探究

## 项目负责人
陈瑭澳222040009 Github：algo23TangaoChen
