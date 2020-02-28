---
layout:     post
title:      阅读笔记（二）
subtitle:    Performance comparison of neural and non-neural approaches to session-based recommendation
date:       2020-02-28
author:     Zbr
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - 神经网络方法
    - 推荐系统
    - 非神经网络方法
---

## 背景

​	神经网络方法在很多领域都有着无可比拟的优势，但现有的对比方法、数据集、评价指标使得新方法的实际进步很难直观理解。因此作者在基于会话机制的推荐系统领域，对神经网络方法和传统方法进行了实验对比，并得出结论：在会话推荐领域现有的神经网络方法提升有限；当使用精准度和召回率参数作为评价指标时，简单方法优于现有神经网络方法。



## 对比方法

#### 神经网络方法

​	选取了四种不使用边信息的顶会方法。

* GRU4REC
* NARM
* STAMP
* NEXTITNET

#### 非神经网络方法

* AR
* SR
* S-KNN
* VS-KNN
* CT



## 数据集

* 电子商务数据集

  * RSC15
  * RETAIL
  * DIGI
  * ZALANDO

* 音乐领域数据集

  * 30MU
  * NOWP
  * AOTM

  将每个数据集按时间分为五个子集，去掉交互仅一次的会话。



## 实验

* 超参优化：应用随机最优化方法迭代一百次找到合适的参数集，所有模型都是针对MRR@20标准优化的
* 预处理：将数据集中近n天作为测试集，其余为训练集
* 评价指标
  * 精准度（P@20）
  * 召回率（R@20）
  * 平均精度（MAP@20）
  * 命中率（HR@20） 
  * 平均倒数排名（MRR@20）。



## 结果

* 电子商务领域
  * 在RETAIL和DIGI数据集上，KNN类方法在所有评价指标上都表现最出色
  * 在ZALANDO数据集上，KNN类方法除了MRR指标其他仍是最佳
  * 只有RSC15数据集上，神经网络方法（NARM）能够一直表现优于最好的非神经网络方法（VS-KNN），最新的CT方法在MRR指标上表现最佳，但最近的STAMP却表现非常差，RSC这个数据集有某种独特的特性
* 音乐领域
  * 在所有数据集上，KNN类方法在命中率、精准度、召回率和平均精度上都表现最佳
  * 在MRR评价指标上，非神经网络的CT方法一直表现最佳，简单方法SR也表现出色，
  * 在神经网络方法中，GRU4REC和NARM表现始终最佳
  * 在MRR评价指标上，KNN类方法一直表现不佳，甚至在AOTM数据集上表现最差
  * STAMP方法在所有对比中都表现最差

