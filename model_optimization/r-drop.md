# R-Drop

> 【NeurIPS2021】R-Drop: Regularized Dropout for Neural Networks
>
> 代码：[https://github.com/dropreg/R-Drop](https://github.com/dropreg/R-Drop)

NeurIPS 2021上，微软亚洲研究院与苏州大学提出了简单有效的正则方法 R-Drop（Regularized Dropout）。R-Drop的思想是：对于同一个样本，**前向传播两次，由于Dropout的存在，会得到两个不同但差异很小的概率分布**，通过在原来的交叉熵损失中加入这两个分布的KL散度损失，来共同进行反向传播，参数更新。（如下图所示）

<figure><img src="https://img-blog.csdnimg.cn/bc4b3800aab341038411a637401f9c2c.jpeg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://img-blog.csdnimg.cn/f70974470d8647568311f7427e9be850.jpeg" alt=""><figcaption></figcaption></figure>

实际实现时，数据不用过两次模型，只需要在同一个 batch 里复制一份即可。对比一下可以发现 Dropout 和 R-Drop 的区别：

* Dropout 希望每一个子模型的输出都接近真实的分布，在测试时，Dropout 关闭使得模型仅在参数空间上进行了平均，因此训练和测试存在不一致性。
* R-Drop 则在训练过程中通过对于子模型之间的输出进行约束，来约束参数空间，让不同的输出都能一致，从而降低了训练和测试的不一致性。

可以看出，整个模型非常简单，作者只做了细微且巧妙的简单转变，可以起到四两拨千斤的作用，大道至简。对于性能，作者在多个CV和NLP领域都做了实验，证明该方法非常有效。具体代码如下：

```
import torch.nn.functional as F
​
# define your task model, which outputs the classifier logits
model = TaskModel()
​
def compute_kl_loss(self, p, q pad_mask=None):
    p_loss = F.kl_div(F.log_softmax(p, dim=-1), F.softmax(q, dim=-1), reduction='none')
    q_loss = F.kl_div(F.log_softmax(q, dim=-1), F.softmax(p, dim=-1), reduction='none')
    # pad_mask is for seq-level tasks
    if pad_mask is not None:
        p_loss.masked_fill_(pad_mask, 0.)
        q_loss.masked_fill_(pad_mask, 0.)
    # You can choose whether to use function "sum" and "mean" depending on your task
    p_loss = p_loss.sum()
    q_loss = q_loss.sum()
    loss = (p_loss + q_loss) / 2
    return loss
​
# keep dropout and forward twice
logits = model(x)
logits2 = model(x)
​
# cross entropy loss for classifier
ce_loss = 0.5 * (cross_entropy_loss(logits, label) + cross_entropy_loss(logits2, label))
kl_loss = compute_kl_loss(logits, logits2)
# carefully choose hyper-parameters
loss = ce_loss + α * kl_loss
```

\
