# 【第四周】MobileNet\_ShuffleNet

## **Part1  论文阅读与视频学习：**

### **MobileNet V1 & V2**

* [MobileNet\_V1\_V2网络讲解](https://www.bilibili.com/video/BV1yE411p7L7)
* [Pytorch搭建MobileNetV2网络](https://www.bilibili.com/video/BV1qE411T7qZ) （有余力的同学可学习代码）

### **MobileNet V3**

* [MobileNet\_V3网络讲解](https://www.bilibili.com/video/BV1GK4y1p7uE)
* [Pytorch搭建MobileNetV3网络](https://www.bilibili.com/video/BV1zT4y1P7pd) （有余力的同学可学习代码）

### ShuffleNet

* [ShuffleNet 网络讲解](https://www.bilibili.com/video/BV15y4y1Y7SY) （ShuffleNetV1掌握就可以了，V2稍微了解下就好）
* 弄清楚 Channel 的 shuffle 是如何用代码实现的

### SENet

* 阅读Momenta公司的《[ImageNet 2017冠军模型SE-Net详解](https://www.momenta.cn/article/20.html)》，掌握 SENet 的基本原理，[代码地址](https://github.com/OUCTheoryGroup/colab\_demo/blob/master/202003\_models/SENet\_CIFAR10.ipynb)

## **Part2  代码作业**

阅读论文《HybridSN: Exploring 3-D–2-DCNN Feature Hierarchy for Hyperspectral Image Classification》，思考3D卷积和2D卷积的区别。并阅读代码（[代码地址](https://github.com/OUCTheoryGroup/colab\_demo/blob/master/202003\_models/HybridSN\_GRSL2020.ipynb)

把代码敲入 Colab 运行，网络部分需要自己完成。

## 思考题

* 训练HybridSN，然后多测试几次，会发现每次分类的结果都不一样，请思考为什么？
* 如果想要进一步提升高光谱图像的分类性能，可以如何改进？
* depth-wise conv 和 分组卷积有什么区别与联系？
* SENet 的注意力是不是可以加在空间位置上？
* 在 ShuffleNet 中，通道的 shuffle 如何用代码实现？
