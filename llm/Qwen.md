### 数据集处理

为提高数据集中的多样性，减少重复数据(Text Duplicate Detection)的影响，这里使用了minhash 算法。  **数据集中存在大量重复数据时，会造成模型容易陷入重复循环中**

- minhash 中应用jaccord系数消除文档中重复的文档内容(利用一个均匀的hash函数，将对应的文档内容映射多个hash值)，总结为基于句子中的重复段落的检测，但是如果单纯使用基于jaccord 进行计算资源存瓶颈。
- 