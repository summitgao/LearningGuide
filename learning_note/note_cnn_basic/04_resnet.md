# ResNet

在VGG中，网络深度达到了19层。在GoogLeNet中，网络史无前例地达到了22层。网络深度能不能进一步加深呢？网络层数增多一般会产生**梯度消失或梯度爆炸问题**。 ResNet 是2015年由当时微软研究院的Kaiming He等提出，通过使用残差学习成功训练出了152层的神经网络，并在**ILSVRC2015比赛中取得冠军**，在top5上的错误率为3.57%，同时参数量大大降低，性能突出。

## 1、Bottleneck结构

ResNet提出使用 residual learning 解决网络退化问题。下图是两种不同的残差结构，左边的结构称为 BasicBlock，右侧的称为 Bottleneck （叫做Bottleneck是因为两边是256个通道，中间是64个通道，像一个bottleneck）。网络中使用的主要是右侧的 Bottleneck，第一层的1× 1的卷积核的作用是对特征矩阵进行降维操作，将特征矩阵的深度由256降为64; 第三层的1× 1的卷积核是对特征矩阵进行升维操作，将特征矩阵的深度由64升成256。 降低特征矩阵的深度主要是为了减少参数的个数。先降维后升维是为了主分支上输出的特征矩阵和 shortcut 分支上输出的特征矩阵形状相同，以便进行加法操作。

<figure><img src="../.gitbook/assets/a86180931c2f429c9a9af5155fdecf3d.jpg" alt=""><figcaption></figcaption></figure>

之所以叫 ResNet，因为正常的网络可以表示为y=H(x)，而残差网络一个残差块可以表示为 H(x)=F(x)+x，也就是 F(x)=H(x)-x，网络模块 F(x) 可以看成是在学习实际输出和输入x之间的残差，所以命名为残差模块。

有了这个结构，我们就可以搭建非常深的网络。下图是 ResNet18 网络的基本结构，观察下图的 ResNet18层网络，可以发现有些残差块的 shortcut 是实线的，而有些则是虚线的。这些虚线的 shortcut 上通过1×1的卷积核进行了维度处理（特征矩阵在长宽方向降采样，深度方向调整成下一层残差结构所需要的channel）。ResNet 还有 34/50/101/152 等多个版本，想详细了解可以参照作者论文。

<figure><img src="../.gitbook/assets/e030e9120b3f4d01819f1e7b7a87bc7d.jpg" alt=""><figcaption></figcaption></figure>

## 2、Batch Normalization

ResNet中还使用了 Batch Normalization (批归一化，BN) 来解决梯度消失和爆炸问题。如下图所示，对于Conv1来说输入的就是满足某一分布的特征矩阵，但对于Conv2而言输入的feature map就不一定满足某一分布规律了（注意这里所说满足某一分布规律并不是指某一个feature map的数据要满足分布规律，理论上是指整个训练样本集所对应feature map的数据要满足分布规律）。而我们Batch Normalization的目的就是使我们的feature map满足均值为0，方差为1的分布规律。

<figure><img src="../.gitbook/assets/e9f1ce6749d249ac84ada5e4c3b5b4eb.jpg" alt=""><figcaption></figcaption></figure>

BN主要是通过计算一个Batch数据的 feature map 然后再进行标准化（batch越大越接近整个数据集的分布，效果越好）。我们根据下图的公式可以知道计算的具体过程。

<figure><img src="../.gitbook/assets/0c9065b0420d40e4803225c62ae1761a.jpg" alt=""><figcaption></figcaption></figure>

B站上有一个超级详细的讲解，推荐大家抽空去看一下 “[ResNet网络结构，BN以及迁移学习详解](https://www.bilibili.com/video/BV1T7411T7wa)”
