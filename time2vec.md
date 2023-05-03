# time2vec详解
## 1. 为什么要使用time2vec
主要是解决对时序数据处理过程中需要人工设计不同的时间窗、滞后算子等手工特征。针对不同问题可能需要设定不同的手工特征，领域知识要求较高。item2vec 中提出一种将时序数据转化为embedding向量。
time2vec 中的三个重要特征:
- embedding结果能够捕获周期数据和非周期数据(==使用周期函数sin、cos进行特征选择==)
- 对时间的变动保持稳定(暂时未看出...)
- 简单易用

## 2. time2vec 使用的原理

$$
\t2v(\tau)[i] = \left\{
    \begin{alined}
    \omega_i\tau + \psi, if
    
}
    $$

## 3. time2vec 适合那些场景



## 4. 可能存在的问题