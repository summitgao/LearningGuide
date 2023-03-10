# VGG网络：更深

牛津大学视觉几何组（Visual Geometry Group）提出了对CNN的深度和其性能进行探索的网络，该网络被命名为VGG。 VGG的结构非常清晰：

* 按照2×2的池化层，网络可以分成若干个块（block）；
* 每个块包含若干个相同的卷积，块内的特征图数量固定不变；
* 特征图的通道数按块以2倍的速度逐渐递增，第四块和第五块内特征图的通道数都是512（即64、128、256、512、512）。

<figure><img src="https://img-blog.csdnimg.cn/e5132963142942839366e8e33812437f.jpeg" alt=""><figcaption></figcaption></figure>

VGG的表现效果也非常好，在2014年的ILSVRC物体分类任务中排名第二（第一名是GoogLeNet），在物体检测任务中排名第一。VGG也是一个非常经典的网络，即使在2023年，阅读CVPR最新论文很多方法仍会将其作为实验对比的backbone。VGG家族的具体设置如下图所示：

<figure><img src="https://img-blog.csdnimg.cn/5c2062841cfd479883f3075ed8a2d900.jpeg" alt=""><figcaption></figcaption></figure>

可以看出，输入均是224X224X3的图像，均采用5层最大值池化，最终生成7X7的feature map，作者认为这是一个比较合适的大小。

卷积完成之后是两个隐层节点数目为4096的全连接层，最后是一个1000类softmax分类器。

B站UP有一个非常详细的介绍 “[VGG网络详解及感受野的计算](https://www.bilibili.com/video/BV1q7411T7Y6)” ，感兴趣可以看看，这里不再过多介绍。
