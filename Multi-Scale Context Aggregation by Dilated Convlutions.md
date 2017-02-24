# Multi-Scale Context Aggregation by Dilated Convlutions



## Background & Motivation:

### Semantic Segmentation :

Model should label every pixel in an image, in this task, the predicted object that has similar size and structure to the input image(dense prediction). 

Long et al.(2015) showed that convolutional network architectures that had originally be developed for image classification can be successfully repurposed for dense prediction.

![](G:\download\学习\Research\imageTypora\p1.png)



### Motivation:

In many such applications one wants to integrate information from different spatial scales and balance two properties:

1. local, pixel-level accuracy, such as precise detection of edges, and
2. integrating knowledge of the wider, global context

To address this problem, people often use some kind of multi-scale convolutional neural networks, which often relies on **spatial pooling**.

But semantic segmentation is challenging because it requires combining pixel-level accuracy with multi-scale contextual reasoning. So which aspects of the repurposed network are truly necessary and which reduce accuracy when operated densely? Can dedicated modules designed specifically for dense prediction improve accuracy further?



### Previous Work:





### In This Work:





## Dilated Convolutions:

Consider a purely convolutional network composed of layers of $k*k$ convolutions, without pooling. It is easy to see that size of the *receptive field* of each unit - the block of pixels which can influence its activation - is l∗(k−1)+kl∗(k−1)+k, where ll is the layer index. So the effective receptive field of units can only grow linearly with layers. This is very limiting, especially for high-resolution input images.

The authors then build a network out of multiple layers of diluted convolutions, where the dilation factor llincreases exponentially at each layer. When you do that, even though the number of parameters grows only linearly with layers, the effective receptive field of units grows exponentially with layer depth($(2^{i+2}-1)(2^{i+2}-1)$). This is illustrated in the figure below:

![](G:\download\学习\Research\imageTypora\p2.png)





## 3.Multi-Scale Context Aggregation:





## 4.Experiments:



## 5.Conclusion:



## 6.Reflections & Questions

