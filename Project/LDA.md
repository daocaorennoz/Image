# LDA

## LDA的简介
LDA的全称是隐狄利克雷分布，是一个在深度学习出来之前非常火的主题模型。是基于贝叶斯先验的。
简单来说就是一个三层模型，主题-文档-单词，其中多个文档对应多个主题，多个单词对应多个文档，最后得出的是每个文档在所有主题下的分布，然后对这个输出的文档表示向量进行计算相似度，然后完成聚类。

很重要的就是计算相似度的方式。
很有名的是余弦相似度，以及KL散度和JS散度。

KL散度是一个非对称的相似度，又称交叉熵，衡量两个分布P和Q之间的差别。KL散度是用来度量使用基于Q的编码来自P的样本平均所需的额外的位元数。
典型情况下，P为真实分布，而Q为待衡量分布，数据的理论分布或者模型分布。
有时也将其称为KL距离，但并不满足距离的对称性以及三角不等式。

而JS散度则是KL散度的变体，解决了其非对称的性质，一般而言JS是对称的，取值范围为0～1之间。