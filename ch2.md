# 生产循环数学定义

上一章简述了生产循环的基本概念和简单例子，这一节我们来尝试用更精确的数学来定义生产循环，进而探究其更多的特性。

生产循环包括要素有生产活动和生产资料。生产资料可简单分为物资和人力。生产活动则包括生产过程和产品。生产过程包括生产要素的投入和产出。产品则包括最终产品和中间产品。

## 生产过程定义

### 生产输入

生产输入定义为向量$x_{生产}$，对应的是生产过程中消耗掉的原料。当然，如果生产输入和输出都有完全相同的物料，也标注输入，例如在煤矿，可能抽水机用的动力也是煤炭，那么在生产过程中还是认为消耗了煤炭。

生产输入采用向量表示，即所有参与生产的原料的集合。如果参考GS1分类码，那么这个向量最大可支持$10^9$种物料输入。

### 生产输出

生产输出定义为向量$y_{生产}$，对应的是生产过程中产生的产品。这个与生产输入类似。其定义域也与生产输入相同。

### 生产资料

生产资料不是生产过程的耗散物资，但也是生产过程的必备物资。生产资料包括人力和物资。人力包括生产者、生产者所拥有的技能、生产者所拥有的知识、生产者所拥有的经验等。物资包括生产过程中所需要的一切物资，如原材料、工具、设备等。
生产资料如果是人造物，则定义域与生产输入和输出相同；
如果是人力资源则需定义特定的工种，按照ISCO（国际标准职业分类），可描述4万种以上的职业；
如果是自然资源，包括土地、空气等，则需定义特定的自然属性。
定义生产资料为向量$M$，包含$M_{人造物}$，$M_{人力}$，$M_{自然资源}$。

### 生产过程

基于上述定义，生产过程可定义为函数$f(\dot)$，单个生产过程描述如下：
$$
\Delta y = f(\Delta x,\tau|M)
$$
这里$\tau$是时延，即当x投入生产过程后，经过一定时间$\tau$后，产出y。如果是单次生产过程，则$f$为跳变函数：
$$
f(x,\tau|M) = \delta (t-\tau-T_0)\cdot \Delta y
$$
其中$\delta(\cdot)$是狄拉克函数，$\Delta y$是生产过程中的产出，即生产过程中产生的产品，其中$T_0$是生产过程的时间，即生产过程从开始到结束的时间。

$$
\delta(t-\tau-T_0) = \begin{cases}
1 & t=\tau+T_0 \\
0 & t\neq \tau+T_0
\end{cases}
$$

如果是周期性生产过程，即隔一段时间生产一批商品，则$f$为周期函数：
$$
f(x,\tau|M) = u(t-k\cdot \tau-T_0)\cdot \Delta y, k\in \mathbb{N}
$$
其中$T_1$是生产周期，即生产过程隔一段时间生产一批商品的时间。

### 生产过程耗散

生产过程耗散定义为向量$\cdot$，对应的是生产过程中消耗掉的原料。生产过程耗散与生产输入相同，但生产过程耗散是生产过程中消耗掉的原料，而生产输入是生产过程中投入的原料。因此，生产过程耗散是生产输入的一部分。

生产过程耗散与生产输入的关系为：
$$
\dot = x_{生产} - y_{生产}
$$

### 生产过程效率

这个仅表述了生产的物资变化，但缺少2个要素：1) 生产资料的折旧损耗；2) 生产时间。同时输入和输出是没有考虑物资的质量，即并不是同一类型的物资都可以相互替代的。因此，我们还需要定义生产过程中的耗散和效率，用时变过程来描述。



## 生产循环定义

### 生产链

矩阵连乘

### 生产环

连乘，导致闭环

### 链和环组成的生产图

图谱

## 生产能力定义

这里需要定义

### 溢出与耗散

循环一周后的剩余。

### 生产效率

时变量，过程耗散率，即单个生产过程的耗散。

速率，单位时间内的产出。

## 货币化衡量

以上内容都未涉及货币描述，是有意为之，特意避开相关的内容。即如果不考虑货币，其实是完全可以的。货币从总体来看，只是人类社群组织内部人员进行生产的一种工具，因此其价格只是人类社群组织内部的一种约定，其本身并不具有价值。货币本身并不具有价值，但货币可以用来衡量价值。因此，货币化衡量只是人类社群组织内部的一种约定，其本身并不具有价值。

但货币确实是人类社会活动（至少到目前为止的文明史）中不可或缺的一种组织方式，而且相当多的生产循环都采用货币化方式进行交易。这种好处是显著降低了交易成本，使得生产效率大大提高，但同时也引入了新的问题。1个显而易见的问题就是货币化是1维的，即价格是多维度信息的1维嵌入，货币化衡量并不能完全反映生产循环的复杂性和多样性。
同时货币的时变、价格的不稳定会导致很多外部因素传递到本来相对独立的生产循环中，使得生产循环的稳定性大大降低。

这里我们尝试构建1种模型，来描述简化的金融行为对生产循环的影响。
