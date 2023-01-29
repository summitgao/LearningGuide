# ShuffleNet

> ShuffleNet: An Extremely Efficient Convolutional Neural Network for Mobile Devices Xiangyu Zhang, Xinyu Zhou, Mengxiao Lin, Jian Sun

ShuffleNet是旷视科技2017年提出的一种计算高效的CNN模型，其和MobileNet和SqueezeNet等一样主要是想应用在移动端。ShuffleNet的核心是采用了两种操作：pointwise group convolution和channel shuffle，这在保持精度的同时大大降低了模型的计算量。

<figure><img src="https://img-blog.csdnimg.cn/05b025f523494d00982757c6a104ccdf.jpeg" alt=""><figcaption></figcaption></figure>

如图所示，(a)的结构类似于 ResNeXt，可以看到各个组之间的特征是不通信的。为了提升各个组间特征的交流，进行了改进，如(b)所示，可以对 group conv 后的特征进行重组，这样下面的 group conv 输入的特征就来自于不同组，本质上，这相当于 channel shuffle，如图(c) 所示，是均匀地打乱顺序。这样编程实现是相当容易的，假定输入特征是 g 组，总通道数是 gxn，首先将通道那个维度拆分为(g,n)两个维度，然后转置变成(n,g)就可以了。如下图所示，就是矩阵变换。

<figure><img src="https://img-blog.csdnimg.cn/3fcb93a046734856b67fb67ed72b684e.jpeg" alt=""><figcaption></figcaption></figure>

代码如下：

```
def channel_shuffle(x, groups):
    # x[batch_size, channels, H, W]
    batch, channels, height, width = x.size()
    channels_per_group = channels // groups  # 每组通道数
    x = x.view(batch, groups, channels_per_group, height, width)
    x = torch.transpose(x, 1, 2).contiguous()
    x = x.view(batch, channels, height, width)
    return x
​
class ChannelShuffle(nn.Module):
    def __init__(self, channels, groups):
        super(ChannelShuffle, self).__init__()
        if channels % groups != 0:
            raise ValueError("通道数必须可以整除组数")
        self.groups = groups
    def forward(self, x):
        return channel_shuffle(x, self.groups)
```

B站网友有非常好的讲解《[ShuffleNetV1, V2详解](https://www.bilibili.com/video/BV15y4y1Y7SY)》，可以结合视频学习。ShuffleNetV2是一篇写的非常精彩的论文，提出了4条设计高效网络的准测，然后以这些准则为指导提出了新的网络，感兴趣可以阅读论文学习。
