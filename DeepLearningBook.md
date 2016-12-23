# Introduction

## AI

人工智能面临的重大挑战是，解决那些人类看起来很容易、直观，但却很难被准确定义的问题，比如：听懂人说话、在图像中识别一张脸等。(Much of this knowledge is subjective and intuitive, and therefor difficult to articulate in a formal way)

AI system need the ability to acquire their own knowledge, by *extracting patterns from raw data*.

## Machine Learning

ML算法的performance很大程度上依赖于**representation of data** they are given.

**表达学习(representation learning)**，就是学习寻找一种好的representation 。例子：autoencoder  

## Deep Learning

**深度学习 Deep learning** solves this central problem in **representation learning** by introducing representations that are expressed in terms of other, simpler representations.  深度学习例子：MLP  多层感知机

但是不是深度学习的每一层都是在做feature (or factor of variation)相关的工作，也有state information，以便于后面可以组合得到有效的输出。

一种定义：Deep learning is a particular kind of machine learning that achieves great power and flexibility by learning to
represent the world as a nested hierarchy of concepts, with each concept defined in relation to simpler concepts, and more abstract representations computed in terms of less abstract ones.

-----

## DL历史

连接主义认为: A large number of simple computational units can achieve intelligent behavior when networked together.

### key concepts  in 1980s:

**distributed representation **:each input to a system should be represented by many features, and each feature should be involved in the representation of many possible inputs. 如红、绿、蓝，车、鸟、衣服，可以有9中组合，用6个神经元来完成（3个表示颜色，3个表示对象类型）。

**back-propagation**:This algorithm has waxed and waned in popularity but as of this writing is currently the dominant approach to training deep models. 至今仍然广泛用于训练深度网络。

**LSTM ** :is widely used for many sequence modeling tasks.

### after then

**deep belief network** (?)  :could be efficiently trained using a strategy called greedy layer-wise pre-training.

### NOW

- Increasing Dataset Sizes

   Working successfully with datasets **smaller** than this is an important research area, focusing in particular on how we can take advantage of large quantities of unlabeled examples, with unsupervised or semi-supervised learning.  研究如何在小数据集上进行学习（你让一个小孩认识苹果，肯定不会给他几万张苹果图片让他去学习）


- Increasing Model Sizes
- Increasing Accuracy, Complexity and Real-World Impact (profitable!)


----



# Linear Algebra

## 2.4 Linear Dependence and Span

对于${Ax=b}$ ,对于所有可能的$b$ 都有解的条件是：$A_{mn}$ 的列空间可以张成整个$R^{m}$ 空间。(n>=m是必要不充分条件)



## 2.5 Norms

- 一般使用$L^{2}$ 范数的平方而不是$L^{2}$ 范数本身，这样对某个元素求导时就不会牵扯上其他元素。但有的机器学习应用中，**区分元素值恰好是零还是非0的小值是很重要的**。平方$L^{2}$ 范数在0附近增长的较慢，所以有时使用$L^{1}$ 范数，增长速率一致。
- $L^{0}$范数（表示向量中非零元素的个数），在数学定义上是不对的，通常用$L^{1}$ 范数来代替。



## 2.6 Special Kinds of Matrices and Vectors

- 不是所有的对角矩阵都是方阵。**长方形的矩阵也有可能是对角矩阵**。长方形对角矩阵没有逆矩阵，但我们仍然可以很快地计算它们的乘法。对于一个长方形对角矩阵 **D **而言，乘法 **Dx **会涉及到 **x **中每个元素的放缩，如果 **D **是瘦长型矩阵，那么在放缩后的向量添加一些零；如果 **D **是胖长型矩阵，那么放缩后去掉最后一些元素。(视情况而定)
- 当某些不依赖参数顺序的两个参数函数生成元素时（some function of two arguments that does not depend on the order of the arguments），对称矩阵经常会出现。例如，如果 **A **一个表示距离的矩阵， $A_{i,j}$表示点 i*到点 j的距离，那么$A_{i,j}=A_{j,i}$*，因为距离函数是对称的。
- 在$R^{n}$ 中，至多有n个范数非零向量互相正交。
- 正交矩阵(orthogonal matrix) 是指行向量是**标准**正交的，列向量是**标准**正交的方阵：$A^{⊤}A= AA^{⊤}=I$


## 2.7 Eigendecomposition

（如果$v$是矩阵$A$的特征向量，$s$是非零实数，那么$sv$也是矩阵$A$的特征向量，且对应特征值相等。所以我们一般只讨论unit eigenvector。）

不是每一个矩阵都可以进行eigendecomposition 分解成特征值和特征向量。在某些情况下，特征分解会涉及到复数，而非全是实数。不过在书中，我们只讨论**实对称矩阵**。而实对称矩阵**一定**可以进行Eigendecomposition：

$A = QΛQ^{T}​$      （按照惯例，通常降序排列$Λ​$中的元素）

其中，Q是由eigenvectors($Q_{:,i}$)组成的正交矩阵，$Λ_{i,i}$对应着$Q_{:,i}$的特征值。因为Q是正交矩阵，我们可以将矩阵A看做(相对于原空间) 沿着$Q_{:,i}即v^{(i)}$方向延展$Λ_{i,i}即\lambda_{i}$倍的空间。

Eigendecomposition可能**不唯一**。因为同一特征值可能对应多个特征向量，在这组特征向量生成的子空间中，任意一组正交向量都是该特征值对应的特征向量。所以，特征分解唯一当且仅当所有特征值唯一。

### Useful Information

- 矩阵是奇异的当且仅当有零特征值。

- 实对称矩阵的eigendecomposition 可以用于优化二次方程$f(x)=x^{T}Ax$， 其中限制$||x||_{2}=1$，在这一限制条件下，函数$f$的最大值是$\lambda_{max}$，最小值是$\lambda_{min}$

  ​


## 2.8 Singular Value Decomposition

**所有的实矩阵都存在SVD分解：**

$A=UDV^{T}$

其中A是m\*n矩阵，U(m\*m)，D(m\*n)，V(n\*n)。U和V都是正交矩阵，D是对角矩阵，不一定是方阵。

The elements along the diagonal of D are known as the **singular values** of the matrix A. The columns of U are known as the **left-singular vectors**. The columns of V are known as as the **right-singular vectors**.

We can actually interpret the singular value decomposition of A in terms of the eigendecomposition of functions of **A**(与A相关) . The left-singular vectors of A are the eigenvectors of $AA^{T}$. The right-singular vectors of A are the eigenvectors of  $A^{T}A$.
The non-zero singular values of A are the square roots of the eigenvalues of $A^{T}A$.The same is true for $AA^{T}$.



## 2.9 The Moore-Penrose Pseudoinverse

基于SVD分解的伪逆：

$A^{+}=VD^{+}U^{T}$

（可用于求解线性方程$Ax=b$）



## 2.10 The Trace Operator

例： $||A||_{F}=\sqrt{tr(AA^{T})}$

(不使用求和符号的话，会很难描述，迹运算可以解决这一问题)



## 2.11 Determinant

行列式，记作 det(**A**)，是一个将方阵 **A **映射到实数的函数。**行列式等于矩阵特征值的乘积。**

行列式的绝对值可以被认为是衡量矩阵相乘后空间扩大或者缩小了多少。如果行列式是 0, 那么空间至少沿着某一维完全收缩了，使其失去了所有的体积。如果行列式是 1, 那么矩阵相乘没有改变空间体积。



## 2.12 Example: PCA(remain)



## Tips:

- 虽然$A^{-1}$在理论分析中很有用(如解方程$Ax=b$)，但是实际中因为精度等问题应**尽量避免求逆**，可以对$A、b$进行变换，然后回代法求得$x$ 。




# Probability and Information Theory


概率论使我们能够**作出不确定的陈述**以及**在不确定性存在的情况下推理**，

而信息论使我们能够**量化**概率分布中的不确定性总量。

## 3.1 Why

Nearly all activities require some ability to reason in the presence of uncertainty.

Machine Learning must always deal with **uncertain quantities**, and sometimes may also need to deal with **stochastic (non-deterministic)** quantities.

不确定性有三种可能的来源：

1. 被建模系统内在的随机性
2. 不完全观测
3. 不完全建模


在很多情况下，使用一些**简单而不确定**的原则要比**复杂而确定**的原则更为实用，即使真实的规则是确定的并且我们的模型系统对适应复杂规则具有很好的逼真度(fidelity)。例如，简单的原则 ‘‘多数鸟儿都会飞’’ 。

The kind of probability related directly to the rates at which events occur, is known as **frequentist probability**(频率概率), while the kind of probability, related to qualitative levels of **certainty**, is known as **Bayesian probability**(贝叶斯概率).


概率可以被看作是用于处理不确定性的逻辑扩展。逻辑提供了一套形式化的规则在给定某些命题是真或假的假设下，判断另外一些命题是真的还是假的。而概率论提供了一套形式化的规则在给定一些命题的似然(likelihood) 后，计算其他命题为真的似然。



## 3.2 Random Variables

随机变量可以是离散的或者连续的。离散型随机变量拥有有限或者可数无限多(如对应自然数)的状态。这些状态不一定非要是整数；它们也可能只是一些被命名的状态并且没有数值。A continuous random variable is associated with a real value.



## 3.3 Probability Distributions

概率分布(probability distribution) 用来描述随机变量或一簇随机变量在每一个可能取到的状态的可能性大小。我们描述概率分布的方式取决于random variables is **discrete** or **continuous**.

### 1. Discrete Variables and Probability Mass Functions（PMF）

离散型变量的概率分布可以用**概率分布律函数 (probability mass function, PMF)**来描述。我们通常用大写字母 **P**来表示概率分布律函数。通常每一个随机变量都会有一个不同的概率分布律函数，并且读者必须根据随机变量来推断所使用的PMF，而不是根据函数的名称来推断；例如， *P*(x) 通常和 *P*(y) 不一样。

有时为了使得PMF的使用不相互混淆，我们会明确写出随机变量的名称： *P*(**x** = *x*)。

### 2.Continuous Variables and Probability Density Functions（PDF）

一个函数 *p*如果想要成为概率密度函数，必须满足下面这几个条件：
• *p*的定义域必须是 x 所有可能状态的集合。
*• **∀ **x∈ x*, p*(*x) ≥ 0. 注意，我们并不要求 p(x) ≤ 1。
*• ∫ p(*x*)*dx *= 1*.

概率密度函数*p*(*x*) 并**没有直接对特定的状态给出概率**，相对的，它给出了**在面积为 δx 的无限小的区域内的概率为 *p*(*x*)*δx***。

Tips:均匀分布$u(x;a,b)$    ";" 表示 ‘‘以什么为参数’’.



## 3.4 Marginal Probability

有时候，我们知道了一组变量的**联合概率分布**，想要了解**其中一个子集的概率分布**。这种定义在子集上的概率分布被称为边缘概率分布(marginal probability distribution)。

例如，假设有离散型随机变量x 和 y，并且我们知道 *P*(x, y)。我们可以依据下面的求和法则(sum rule) 来计算 *P*(x)：
![](G:\download\学习\Research\imageTypora\3.jpg)

![](G:\download\学习\Research\imageTypora\4.jpg)



## 3.5 Conditional Probability

![](G:\download\学习\Research\imageTypora\5.jpg)



## 3.6 The Chain Rule of Conditional Probabilities

**任何多维随机变量的联合概率分布，都可以分解成只有一个变量的条件概率相乘。**

![](G:\download\学习\Research\imageTypora\6.jpg)



## 3.7 Independence and Conditional Independence

搞清楚独立和条件独立的概念。



## 3.8 Expectations, Variance and Covariance

![](G:\download\学习\Research\imageTypora\9.jpg)

期望是线性的。可以线性相加或乘以一个标量。

![](G:\download\学习\Research\imageTypora\10.jpg)



**区分独立、协方差为0**：协方差为0是指没有**线性**关系，但不代表没有非线性关系，所以不一定独立。



## 3.9 Common Probability Distributions

Bernoulli Distribution

Multinoulli Distribution

Gaussian Distribution

![](G:\download\学习\Research\imageTypora\13.jpg)

Exponential and Laplace Distributions

The Dirac Distributions and Empirical Distributions

### Mixtures of Distribution

存在latent variable，即超参数，不能直接观测。

高斯混合模型是万能逼近器。因为理论上，任何**平滑的**概率密度都可以用具有足够多组件的高斯混合模以任意精度来逼近。



## 3.10 Useful Properties of Common Functions

Sigmoid

softplus:

![](G:\download\学习\Research\imageTypora\14.jpg)

![](G:\download\学习\Research\imageTypora\15.jpg)

![](G:\download\学习\Research\imageTypora\16.jpg)

# 我的问题：

pre-learning

左逆右逆

情况之：quared L^2 norm may be undesirable because it increases very slowly near the origin.  In several machine learning applications, it is important to **discriminate between elements that are exactly zero and elements that are small but nonzero**.

In many cases, we may derive some very general machine learning algorithm in terms of arbitrary matrices, but obtain a less expensive (and less descriptive) algorithm by restricting some matrices to be diagonal.在很多情况下，我们可以根据任意矩阵导出一些通用的机器学习算法；但通过将一些矩阵限制为对角矩阵，我们可以得到计算代价较低的（并且描述语言较少的）算法。 【什么情况？】



![](G:\download\学习\Research\imageTypora\12.jpg)















