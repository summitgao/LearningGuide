# LN和IN

## 1、LayerNorm (LN)

当batch size较小时，应用BN会性能一般，原因是计算归一化统计量时样本数太少。LN是一个独立于批次的算法，无论样本数多少都不会影响LN计算的数据量。在最近的 Vision Transformer 模型中，大多放弃BN，而使用 LN 来取得好的效果。因为LN比BN慢，BN推理阶段不用重新计算均值方差，可以合并到卷积中（也就是所谓的吸BN）。

目前无论是CV还是MLP中应用，LN都是在 channel 维度归一化。在CNN中，大多需要结合BN，因为实验中发现 LN 会破坏卷积学习到的特征，效果不如 BN。

## 2、InstanceNorm (IN)

LN 和 BN 主要应用于图像分类，但是对于 图像修复、风格迁移等应用，需要统计的是单张图片的信息，Batch Norm 会破坏单张图片的统计特性，因此一般使用 Instance Norm 。

在 Arbitrary Style Transfer in Real-time with Adaptive Instance Normalization，CVPR2017 这个风格迁移的工作中，作者提出 IN本质上是一种Style Normalization，它的作用相当于把不同的图片统一成一种风格。（风格迁移如下图所示）

<figure><img src="../.gitbook/assets/微信截图_20230129235859.jpg" alt=""><figcaption></figcaption></figure>

作者提出，图像的风格（artistic style）就是特征图各个feature channel跨空间的统计信息，比如mean和variance。迁移各个channel的mean和variance就可以实现风格迁移，为此他们提出了Adaptive Instance Normalization。这是一个非常著名的工作，感兴趣可以阅读。



