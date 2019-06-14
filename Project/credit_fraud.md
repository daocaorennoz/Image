
# 严重非平衡样本集下的信用卡欺诈预测

## 任务背景

对于给定的数据集训练模型来预测信用卡行为是否为欺诈行为

## 数据探索
- 给定了284807条记录共30维特征、1维为标签作为数据集。

- 原始特征：

28维经过PCA降维的特征，分别是V1-V28，加上Amount（金额）和Time（时间）两个维度，共30维

- 标签：

0代表正常行为
1代表欺诈行为

- 样本初始比例：

284315： 492换算成比例为：99.83%：0.17%

## 特征工程

由于给定的特征是经过PCA处理过的，没有办法获得原有的数据信息，以及代表的意思。所以难以建立组合特征。

- 通过可视化得到数据中各个维度之间的相关系数。为之后的特征筛选做准备。

- 通过柱状图来区别查看诈骗事件和正常时间在各特征维度上的分布，挑选出区分度比较大的特征作为备选

- 利用随机森林的模型得到各特征的重要性系数，结合之前做出的特征选择的准备，做出特征选择

## 数据处理

运用SMOTE合成算法，平衡不平衡的样本集。

SMOTE算法是利用KNN算法，选择少数样本附近的K个同类样本点，随即插值得到新的样本，然后将新的样本与原数据合成，长生新的平衡的训练集。

## 训练模型

然后利用Xgboost模型，利用GridSearch的参数搜索方法选择合适的参数，最后得到93.73的召回

我还尝试了另外一种不平衡数据集的处理方法，将正负类样本的权重设置为各自比例的倒数，然后将所有特征进行归一化，利用轻量级深度学习框架keras来搭建模型，实际上也就是三层加上dropout的全连接，训练80轮之后大致就收敛了，此时的召回和准确率均不及上一种方法。


