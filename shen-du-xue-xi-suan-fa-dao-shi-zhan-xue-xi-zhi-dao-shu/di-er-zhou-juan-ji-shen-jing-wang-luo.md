---
description: 卷积神经网络基础：卷积、池化、全连接、AlexNet、VGG、GoogleNet、ResNet
---

# 【第二周】卷积神经网络

## **1. 视频学习**

学习专知课程《卷积神经网络》，主要内容包括：

* CNN的基本结构：卷积、池化、全连接
* 典型的网络结构：AlexNet、VGG、GoogleNet、ResNet

## **2. 代码练习**

需要使用谷歌的 Colab ，大家有任何问题可以随时在群里 AT 我。有部分同学已经做过这部分代码练习，可以略过。

* MNIST 数据集分类：构建简单的CNN对 mnist 数据集进行分类。同时，还会在实验中学习池化与卷积操作的基本作用。链接：[https://github.com/OUCTheoryGroup/colab\_demo/blob/master/05\_01\_ConvNet.ipynb](https://github.com/OUCTheoryGroup/colab\_demo/blob/master/05\_01\_ConvNet.ipynb)
* CIFAR10 数据集分类：使用 CNN 对 CIFAR10 数据集进行分类，链接：[https://github.com/OUCTheoryGroup/colab\_demo/blob/master/05\_02\_CNN\_CIFAR10.ipynb](https://github.com/OUCTheoryGroup/colab\_demo/blob/master/05\_02\_CNN\_CIFAR10.ipynb)
* 使用 VGG16 对 CIFAR10 分类，链接：[https://github.com/OUCTheoryGroup/colab\_demo/blob/master/05\_03\_VGG\_CIFAR10.ipynb](https://github.com/OUCTheoryGroup/colab\_demo/blob/master/05\_03\_VGG\_CIFAR10.ipynb)

## 3. 博客作业

【第一部分：代码练习】在谷歌 Colab 上完成上面的代码练习，关键步骤截图，并附一些自己的想法和解读。

【第二部分：问题总结】思考下面的问题：\
1、dataloader 里面 shuffle 取不同值有什么区别？\
2、transform 里，取了不同值，这个有什么区别？\
3、epoch 和 batch 的区别？\
4、1x1的卷积和 FC 有什么区别？主要起什么作用？\
5、residual leanring 为什么能够提升准确率？\
6、代码练习二里，网络和1989年 Lecun 提出的 LeNet 有什么区别？\
7、代码练习二里，卷积以后feature map 尺寸会变小，如何应用 Residual Learning?\
8、有什么方法可以进一步提升准确率？

如果还有其它问题，可以总结一下，写在博客里，下周一起讨论。



_<mark style="color:red;">**热爱学习，拒绝划水 \~\~\~**</mark>_&#x20;
