Big_Data_Contest
================

# [图像搜索竞赛](http://www.pkbigdata.com/c/00000000057/)

## 任务描述

参赛队伍需要开发图片搜索程序，为图片库建立索引，再用查询图片进行搜索。每次用1张图片进行查询，得到`50`条搜索结果，按照相关度从高到低排序。总共有`6`次查询，`300`条搜索结果。结果以`csv`格式文件提交。

## 数据集描述

1. 图片库
  - 第一组：`15`万张女装图片，其中有`30`张目标图片，图片命名为`clothes_id`。
  - 第二组：`15`万张鞋图片，其中有`30`张目标图片，图片命名为`shoes_id`。

2. 查询图片
  - 第一组：`3`张女装图片，图片命名为`clothes_id`。
  - 第二组：`3`张鞋图片，图片命名为`shoes_id`。

目标图片是指我们希望参赛队伍搜索出的图片。每张查询图片对应有十张目标图片。

### 获取数据的方式

百度云网盘：http://pan.baidu.com/share/link?shareid=3724932786&uk=2404571876&third=15

注:本次比赛所用数据集均来源于互联网，仅用于本次竞赛的分析、建模用途，不得用于其他用途，竞赛委员会不具有拥有和授权权利。

## 提交数据格式

参赛队伍提交的数据包含两列，第一列为`source_img`（查询图片），第二列为`target_img`（搜索结果），列与列之间用逗号隔开。每一行代表一个搜索结果，比如第一行`clothes_250001.jpg`, `clothes_100000.jpg`，代表用名为`clothes_250001.jpg`的图片搜索到了名为`clothes_100000.jpg`的图片，且该图片的排序为第一位。每张查询图片有`50`个搜索结果，则需用`50`行来保存结果，按相关度从高到低排序。

可参看提交数据的[demo](http://www.pkbigdata.com/Uploads/competitions/5465d68bb4343.csv)。

注：提交的第一行数据必须为`source_img`, `target_img`。

### 数据文件

| 文件名 | 所有格式 |
| ------ | -------- |
| demo.csv | [csv (10.86kb)](http://www.pkbigdata.com/Uploads/competitions/5465d68bb4343.csv) |

## 评分方法

我们用Normalized Discounted Cumulative Gain（NDCG）来评价搜索结果的质量。6次搜索的结果，有6个NDCG值来评价其质量。最终成绩为6个NDCG值的加权平均数。

### 计算步骤如下：

- 第一步，计算DCG
  
  一个有`p (p ≥ 2)`个结果的搜索结果页面的DCG定义为：
  
  ![DCG](http://www.pkbigdata.com/Uploads/competitions/5465c30035b35.gif)
  
  `p`是指每次搜索返回的结果数（即`50`）。`reli`指的是检索出的图片中排序为`i`的图片的相关度等级。图片库中，对于每一张查询图片，其对应的目标图片的相关度为`2`，其余图片的相关度为`0`。

- 第二步，计算`NDCG`
  
  ![NDCG](http://www.pkbigdata.com/Uploads/competitions/5465c35e7b7f9.gif)
  
  其中`IDCG`是针对某一查询的理想的`DCG`值。

- 第三步，计算`6`个`NDCG`值的加权平均数
  
  ![NDCG](http://www.pkbigdata.com/Uploads/competitions/5465c369eb1c2.gif)

  其中`m`表示第一组数据的查询次数，值为`3`；`n`表示第二组数据的查询次数，值为`3`。第一组结果的`NDCG`值占总成绩的`60%`，第二组结果的`NDCG`值占总成绩的`40%`。

## 预定指标

比赛成绩——`NDCG`的加权平均数大于等于`0.2`，视为达标。

## 比赛规则

- 每支队伍最多包含`5`名成员

- 每支队伍每天最多提交`2`次

- 每支队伍只能选2次提交作为最终提交

1. 赛事委员会会预设一个成绩指标，若达标的参赛队伍超过五支，选择排名前五的队伍进入答辩环节；若有参赛队伍的成绩达标而达标的队伍数不足五支，则达标的参赛队伍进入答辩环节；若没有参赛队伍的成绩达标，则没有队伍进入答辩环节。

2. 赛事委员会会验证成绩前五的参赛队伍的程序有效性，若发现有作弊的行为，取消该参赛队伍的参赛资格及奖励，因此，参赛队由于使用投机方法或者人工手段提交成绩的，视为作废。最终有效成绩进行从高到低排名，选取其他成绩达标的参赛队伍进入答辩环节。

## 比赛奖励

我们预设了一个比赛成绩指标，成绩达标与否将影响参赛队伍获得的奖励。

1. 进入答辩的队伍，依据其最终比赛名次，奖励如下：
  - 第一名：人民币`30000`元；
  - 第二名：人民币`10000`元；
  - 第三名：人民币`5000`元；
  - 第四名：人民币`3000`元；
  - 第五名：人民币`2000`元

2. 若没有队伍进入答辩，则对排名靠前的队伍予以鼓励：
  - 第一名：人民币`2000`元；
  - 第二名：人民币`1000`元；
  - 第三名：人民币`1000`元；
  - 第四名：人民币`500`元；
  - 第五名：人民币`500`元

## 参赛作品提交

最终排名前五的参赛队伍需要提交以下材料至此邮箱contest@unionbigdata.com：

- 代码及代码说明；
- 问题解决方案的详细说明文档；
- 运行结果

## [排行榜](http://www.pkbigdata.com/c/00000000057/leaderboard)
