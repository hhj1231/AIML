# 王振宇 step9总结
## step 9（）RNN  循环神经网络
在普通循环神经网络部分，我们将先介绍只有两个时间步的网络，然后扩展到四个时间步，通过软件工程的抽象，进一步扩展到通用的网络模型。然后介绍不定长时序循环神经网络、深度循环神经网络、双向循环神经网络。通过这一部分的学习，使读者对于循环神经网络的基本原理有透彻的理解。

在高级循环神经网络部分，将介绍LSTM、GRU、序列到序列的模型的原理，为以后学习自然语言处理（Natural Language Processing，NLP）打下坚实的基础。
* 普通循环神经网络
  - 一对多的结构
  在国外，用户可以指定一个风格，或者一段旋律，让机器自动生成一段具有巴赫风格的乐曲。在中国，有藏头诗的娱乐形式，比如以“春”字开头的一句五言绝句可以是“春眠不觉晓”、“春草细还生”等等。这两个例子都是只给出一个输入，生成多个输出的情况。
  - 多对一的结构
  在阅读一段影评后，会判断出该观众对所评价的电影的基本印象如何，比如是积极的评价还是消极的评价，反映在数值上就是给5颗星还是只给1颗星。在这个例子中，输入是一段话，可以拆成很多句或者很多词组，输出则是一个分类结果。这是一个多个输入单个输出的形式。
  - 多对多（输入输出等量）
  这种结构要求输入的数据时间步的数量和输出的数据的时间步的数量相同
  - 多对多（输入输出不等量）
  这是循环神经网络最重要的一个变种，又叫做编码解码（Encoder-Decoder）模型，或者序列到序列（seqence to seqence）模型
* 高级循环神经网络
  三种网络模型：
    - 长短时记忆网络（LSTM）
        长短时记忆网络（LSTM）是最先提出的改进算法，由于门控单元的引入，从根本上解决了梯度爆炸和消失的问题，使网络可以处理长距离依赖。
    - 门控循环单元网络（GRU）
        LSTM网络结构中有三个门控单元和两个状态，参数较多，实现复杂。为此，针对LSTM提出了许多变体，其中门控循环单元网络是最流行的一种，它将三个门减少为两个，状态也只保留一个，和普通循环神经网络保持一致。
    - 序列到序列网络（Sequence-to-Sequence）
        LSTM与其变体很好地解决了网络中梯度爆炸和消失的问题。但LSTM有一个缺陷，无法处理输入和输出序列不等长的问题，为此提出了序列到序列（Sequence-to-Sequence, 简称Seq2Seq）模型，引入和编码解码机制（Encoder-Decoder），在机器翻译等领域取得了很大的成果，进一步提升了循环神经网络的处理范围。