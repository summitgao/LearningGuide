# 科研做图指导

{% hint style="info" %}
首先介绍两个资源：

* Tips for Writing a Research Paper using LaTeX，[https://github.com/guanyingc/latex\_paper\_writing\_tips](https://github.com/guanyingc/latex\_paper\_writing\_tips) 由陈冠英老师维护，给LaTeX初学者提供多个图表排版的例子，方便用到自己的论文当中。[知乎文章](https://zhuanlan.zhihu.com/p/435701387)
* [ML Visuals](https://github.com/dair-ai/ml-visuals)，里面包含100多个常用的神经网络的图，是google在线PPT的形式，[下载地址](https://docs.google.com/presentation/d/11mR1nkIR9fbHegFkcFq8z9oDQ5sjv8E3JJp1LfLGKuk/edit?usp=sharing)
{% endhint %}

审稿人看论文时非常容易关注论文里的图。论文里的图就是“第一印象”，规范的、高质量的图片是发表高水平文章的必备条件。个人感觉，论文里的图基本分为两种：模型图、数据展示图。

* **模型图：**论文的总体框架图、模块细节图、流程图等
* **数据展示图：** 展示数据的折线图、柱状图、散点图等

无论是哪种图，参考最近的CV顶会论文，配色一般是淡蓝、淡红、淡黄、淡绿 四种，有时会用 紫色、灰色补充（紫色多用于模块，灰色多用于小区域或者大面积打底）。整个论文的配色风格需要一致，比如说后面的折线图、柱状图、散点图最好还是以前面框架的颜色一致。（如果前面模型图是淡蓝色，后面再出现过于鲜艳的其它颜色就有些突兀）

下面展示一些典型模型图的例子：

<figure><img src="https://img-blog.csdnimg.cn/68bb7c116b284137946892b545ac22ad.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/7b084e5b191d4c93b2c87f2543507f39.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/35946474d10b48c4950dce49b464e812.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/e6ef00159dc148b1afd1e2eb24987f8a.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/af1bc947e21449cd9c1eedae7dc07c80.png" alt=""><figcaption></figcaption></figure>

下面展示一些典型数据展示图的例子：

<figure><img src="https://img-blog.csdnimg.cn/9e1ff455077a466c856db61f605e59bc.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/d9dc039dad304438932887dfda9a9c57.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/f283259125974c1ea51a0c75da9d9bee.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/c53e5d7110764462aefef4291b8fe6f9.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/778c06170e284a7f902eef95f6177d77.png" alt=""><figcaption></figcaption></figure>

## 1、模型图

论文里的模型架构图一般我会使用PPT来画。下面的图来自Yongming Rao 在 ECCV2022的AMixer，使用PPT画下面的图是毫无压力的。这个图里也体现了一些作者的一些作图习惯。比如，图里不要出现过多的色彩，以蓝、黄、绿、红为主（色调都比较淡）。

推荐大家也多找一些优秀的论文图为模板，里面的颜色可以用截图来取（ALT+A可以调用微信的截图工具，能够看到每个元素的RGB色调）。也可以把图片粘贴到PPT里，用PPT里的滴管工具来取色。

![请添加图片描述](https://img-blog.csdnimg.cn/af0ce060785a407fbb95e6dccec80986.png)

我也阅读了Rao老师其它的论文，可以看到，他的论文绘图风格使用的色调、整体风格还是比较一致。

下图是CVPR022的DenseClip：

![请添加图片描述](https://img-blog.csdnimg.cn/6884a28e3f594ec3893774b6ed9b428d.png)

下图是NeurIPS2022 的 P2P：

![请添加图片描述](https://img-blog.csdnimg.cn/ba2c9a13811b42b4b8233a06818cfb45.png)

这些图都是可以用PPT画出来的。需要注意的是：（1）色调不会很深，给人很舒服的感觉；（2）论文中需要给多个模块绘图，或者出现折线图、柱状图，颜色字体风格要前后一致。如果不一致会给人感觉很突兀。比如NeurIPS2022的P2P，因为使用了蓝、绿、紫、红、黄，在后面的实验里仍然使用这些颜色绘制柱状图，颜色字体也没有发生变化，风格非常一致（如下图）。（3）PPT文件可以直接导出为PDF，使用软件裁剪后即可插入到论文中，这样插入到论文里的是矢量图，效果非常好。

![P2P实验部分图](https://img-blog.csdnimg.cn/7d5425cc751b467c9463304e7bfb4ea9.png)

![P2P实验部分图](https://img-blog.csdnimg.cn/a9007d0ebfa34091b2cc3dc0417200a3.png)



## 2、数据展示图

除了模型架构图以外，常用的折线图、柱状图、散点图等等，我建议使用 AxGlyph 来绘制，官网：[https://www.amyxun.com/](https://www.amyxun.com/) 这是一个收费软件，价格为 36元，不是特别贵，可以支持一下国产软件。

下图是我用AxGlyph画的一个折线图供大家参考，[下载地址](https://gaopursuit.oss-cn-beijing.aliyuncs.com/2023/demo\_line.agx)。

<figure><img src="https://img-blog.csdnimg.cn/593134700ac74d379d22caad660b2dae.png" alt=""><figcaption></figcaption></figure>

下图是我用AxGlyph画的一个柱状图供大家参考，[下载地址](https://gaopursuit.oss-cn-beijing.aliyuncs.com/2023/demo\_histo.agx)。

<figure><img src="https://img-blog.csdnimg.cn/051a5a05319b4e19abeda30b9a5fc82d.png" alt=""><figcaption></figcaption></figure>

当同时在论文里需要多个数据图、拆线图时，颜色也可以适当变化，如下图所示，效果也不错。

<figure><img src="https://img-blog.csdnimg.cn/5cbfe8fa6e4a4729ad6830597573f746.png" alt=""><figcaption></figcaption></figure>

可以看出，AxGlyph绘制的图，是比 office 默认要美观的，而且支持直接导出为PDF，可以以矢量的形式直接在论文里使用。我最近论文里的一些展示数据的图也都是用AxGlyph绘制（如下图），效果比较好，所以向大家推荐这个工具。

![请添加图片描述](https://img-blog.csdnimg.cn/d3c92c46cab040ac9d1103f0d4d23877.png)



## 3、总结

个人感觉，正常的科研做图，用好PPT（画框架）和 AxGlyph（画数据），完全足够了。科研人员就像作家写小说，展示出来好的内容给读者。必须承认，就跟导演拍电影一样，需要天份，天份高的拍出来好看，天份不够的拍出来难看。

但是，模仿别人的论文做图风格，使用别人的论文做图配色，是不算抄袭的。建议大家以某个学者的论文为模板多积累，坚持下去会显著提高水平。
