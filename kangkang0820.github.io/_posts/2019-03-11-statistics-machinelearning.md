---
title: "机器学习之统计基础"
layout: post
category: ML
tags: [机器学习,算法,基本术语]
excerpt: "前两天看到一篇系统介绍机器学习进阶学习的资料，感觉上面说到的步骤的可操作性还是比较强的，因此想以记笔记的方式来加强学习效果。"
---
前两天看到一篇系统介绍机器学习进阶学习的资料，感觉上面说到的步骤的可操作性还是比较强的，因此想以记笔记的方式来加强学习效果。
# Chapter 1 鸟瞰思维
## 机器学习 ≠ 算法
机器学习并不是关于算法的，机器学习是关于问题解决的综合性方法，而单独的算法只是这个综合性问题的一小块，问题剩下的部分是关于如何正确的运用算法。
## 什么使得机器学习变得如此特殊？
机器学习就是教会电脑如何从数据中学习到特定的模式从而做出决策或者预测，对于真正的机器学习，电脑必须能够学习到无法用显示程序识别的模式。

__例子：好奇的小孩__

一小孩在家玩耍...当他看到一支燃烧的蜡烛的时候，他好奇的走过去。1.出于好奇，他把手伸向蜡烛的火焰。2."哎哟！"他叫出声来，并迅速的缩回手。3.“嗯...那个红色的发光的东西原来是可以伤人的！”。两天以后，他在厨房玩耍...他看到厨房燃烧的炉子，他再次好奇的走过去。1.他是好奇心再次爆发，想着把手伸过去。2.突然，他意识到炉面是“红色的、发光的”。3.“啊！”他突然有所顿悟“今天可不能在这样了”。4.他回想起来了“红色的发光的东西会让人感到疼痛的”，然后他就离开了炉子。

非常明确，这里只包含机器学习，因为小孩从蜡烛里学习到了模式：
- 他学习到了“红色的发光的东西会让人感到疼痛的”
- 另一方面，如果他仅仅是因为父母的警告而离开炉子，那就是“显示程序”（explicit programming）而非机器学习了。

## 关键术语

- __模型（Model）__： 从数据中学习到的一系列模式
- __算法（Algorithm）__： 用来训练模型的特殊的机器学习方法
- __训练集（Training data）__： 算法用来训练模型的数据库
- __测试集(Test data)__： 用来评估模型的新数据库
- __特征值（Features）__： 数据库中用来训练模型的变量（列）
- __目标值（Target variable）__： 用于预测的特殊变量
- __观测值（Observations）__： 数据库中的数据点（排）

__例子：小学生__

![primary-school-example-terms](/images/posts/20190311/primary-school-example-terms.jpg)

例如，你手上有一批150人的小学生信息数据库，并且你想用这些学生的年龄、性别和体重等来预测他们的身高

- 你有150个观测值
- 一个目标值（身高）
- 3个特征值（年龄、性别、体重）
- 你可以把你的数据分为两部分：1.其中的120人作为数据库来训练模型（训练集） 2.剩下的30人用来选择最佳模型（测试集）

## 机器学习的任务

学术界的机器学习专注于算法研究。然而，在实际应用中，你应该首先关注的机器学习的任务。
- 任务就是你的算法的特殊对象
- 只要任务明确了，算法是可以随时换动的
- 实际上，你应该经常尝试不同的算法，因为你并不知道哪一种算法和你的数据是最匹配的
在机器学习中，最常见的两种任务分类是：监督学习和非监督学习

### 监督学习（Supervised Learning）

监督学习是针对有“标签”的数据而言的，它具有以下特征：
- 经常被当作预测模型的高级形式
- 每一个观测值都有“确定的答案”
- 你需要建立一个预测模型，因为在训练的时候你必须告诉算法什么是“正确的”
- __回归__ 任务是针对连续目标变量进行建模的
- __分类__ 任务是针对分类目标变量进行建模的

![weaker-penalty-noisy-conditional](/images/posts/20190311/weaker-penalty-noisy-conditional.png)

### 非监督学习（Unsupervised Learning）

非监督学习包含的任务是“无标签”数据（没有目标值），它具有如下特征：
- 在实际应用中，它经常被用作为自动数据分析或者自动的信号提取
- 无标签数据没有事先的“正确答案”
- 允许算法直接从数据中学习模式（‘不受监督’）
- __集群__ 是最常见的非监督学习任务，它用于在数据中区分组

![mlmc-cluster-analysis](/images/posts/20190311/mlmc-cluster-analysis.png)

## 机器学习的三要素

### 1.一位经验丰富的厨师（A skilled chef）

首先，尽管我们是“教电脑自身如何去学习”，但是人类的指导起着巨大的作用。
- 正如你所知道的那样，你需要不断的做出决择
- 实际上，第一个重要的决择就是如何指定一个能确保你的项目成功的路线图

### 2.新鲜的食材（Fresh ingredients）

第二个重要的因素就是数据本身的质量
- 垃圾的数据必然产生垃圾结果，不管你用哪种算法
- 专业的数据分析师一定是在理解数据、清洗数据和挖掘新特征上花最多的时间

### 3.避免烹调过度（Don't overcook it）

机器学习中最危险的一个陷阱就是过度拟合。一个过度拟合的模型“记住”的是训练集中的噪音，而不是学习真正的潜在模式。
- 对冲基金中的过度拟合模型可以导致数百万美元的损失
- 医院中的过度拟合模型可能使成千上万人丧命
- 虽然在大多数的实际应用当中，过度拟合模型不会造成如此大的灾难，但是它仍然是你要竭力避免的严重错误

## 蓝图

机器学习的5大核心步骤：

- __1.探索分析（Exploratory Analysis）__ 首先，你必须要“理解”数据。这一步一定要快！快！快！！！
- __2.数据清洗（Data Cleaning）__ 其次，清洗你的数据可以避免很多常见的陷阱，好的数据胜过优秀的算法
- __3.特征提取（Feature Engineering）__ 再次，通过挖掘新的特征来帮助你的算法聚焦于什么是重要的
- __4.算法选择（Algorithm Selection）__ 在最短的时间里选择最优、最合适的算法
- __5.模型训练（Model Training）__ 最后，训练你的模型。只要你前面的4步完成了，这一步就很公式化了。

![What-Goes-Into-a-Successful-Model](/images/posts/20190311/What-Goes-Into-a-Successful-Model.jpg)

机器学习不应该是随机的、零碎的，而是系统的、有组织的。另外，即使你一点都不记得前面讲的内容，记住“好的数据比优秀的算法跟重要”。

__补充阅读：__

数据分析师应避免犯的9个错误<https://elitedatascience.com/beginner-mistakes>

给入门者的65+免费科学数据资源<https://elitedatascience.com/data-science-resources>

Python机器学习教程<https://elitedatascience.com/python-machine-learning-tutorial-scikit-learn>

# Chapter 2 探索分析
## 为什么要提前探索数据集？
探索数据集的目的是“了解”这个数据集。提前探索数据集可以使接下来的步骤更顺畅，主要包括一下3个方面：

1.可以为数据清洗获取有价值的提示

2.可以为之后的特征提取寻找灵感

3.可以使你对数据有“感觉”，这将对之后的结果产出有重要的影响

然而，数据探索的步骤应该迅速、高效、果断...不要深陷！
不要跳过这一步，不过也不要陷入其中。

## 从最基础的开始
首先，你应该回答有关这个数据集的一些基本问题：
- 我拥有多少观测值？
- 有多少特征值？
- 我的特征值是什么样的数据类型？是数值型的还是分类型的？
- 有目标值吗？

## 画数据分布图
通常情况下，一个简单的 __直方图__ 就足够理解数据的分布了，有以下事项需要特别注意：
- 意料之外的分布
- 潜在的不合理的异常值
- 特征值应该是二进制的
- 界线没有意义
- 潜在的测量误差

![histogram-grid-example](/images/posts/20190311/histogram-grid-example.png)

从现在开始，你应该开始记录你想要做出的修改。如果有些看起来不太合适的东西，比如特征值中有潜在的异常值，那么现在是告诉客户的好时机，或者进一步深度挖掘。

## 画分类分布图
分类型的数据就不能用直方图来展示，而要用条形图。特别的，你需要提防稀疏类，这种类具有很少的观测值。需要强调的是，“类”只是分类特征中的一种特定值。例如，下面的条形图展示的是被称为“exterior_walls”的特征值的分布，所以像 Wood Siding, Brick, 和 Stucco 就是这个特征值的每一个类。

![grouping-sparse-classes-before](/images/posts/20190311/grouping-sparse-classes-before.png)

现在，我们再返回谈谈稀疏类...正如你看到的那样，“exterior_walls” 的一些类的条状的长度很短，它们就是稀疏类。它们会给建模的时候带来一些麻烦。
- 如果情况好的话，它们不会对模型造成多大的影响。
- 如果情况不好的话，它们将造成模型的过度拟合。

因此，我们建议在后面对这些类进行组合和重新分配的时候做下注释。我们一般会将这些注释一直保存到特征加工。

## 画分段图
画分段图是观察分类型特征值和数值型特征值之间关系的有效方法，箱形图可以帮你做到。以下是你可以从下图中得到的一些见解：
- 单户交易额的中间值远比公寓/别墅要高
- 两种类的最大和最小交易额是想当的
- 事实上，整数型最小值（$200k）和最大值（$800k）表明可能存在数据截断...
- 记住这个在之后评估你的模型通用性的时候非常重要

![boxplot-segmentation-example](/images/posts/20190311/boxplot-segmentation-example.png)

## 研究相关
最后，相关分析可以让你了解数据特征值和其它特征值之间的关系。相关是一个介于-1和1之间的值，它表示的是两个特征值在改变的过程中的紧密程度：
- 正相关表示的是一个特征值随着另一个特征值的增大而增大
- 负相关表示的是一个特征值随着另一个特征值的增大而减小
- 相关系数接近-1或者1表示两个变量之间具有很强的关系
- 相关系数接近0表示两个变量之间的关系很弱
- 相关系数为0表示两个变量之间没有关系

相关 __热力图__ 可以让你的数据信息变得可视化
![correlations-heatmap-example](/images/posts/20190311/correlations-heatmap-example.png)
通常，你需要留意以下信息：
- 哪一个特征值与目标值具有较强的相关
- 对其它特征值之间的强相关感兴趣或者有所期待吗？

再次强调，你的目标是获取对数据的“感觉”，这可以让后面的工作更顺畅。

补充阅读：

使用Python进行数据的可视化<https://elitedatascience.com/python-seaborn-tutorial>

# Chapter 3 数据清洗
## 好的数据 > 漂亮的算法
- 数据
