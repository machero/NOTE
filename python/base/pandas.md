



dataFrame.to_numpy 是输出底层数据的Numpy对象，并不会复制数据。





DataFrame.loc() 按照标签选择某一条数据

```

df.loc[dates[0]]按照标签选择某一条数据
df.loc[:, ['A', 'B']] 按照标签选择某些列
```





df.loc 和df.at 中前一个能够进行切片，后一个只能选择行或者列，*对应的at 后的值为一个标量*

df.iloc只能根据位置进行查找

```python
df.iloc[3]
```

 `Series.array`则只返回 `ExtensionArray`，且不会复制数据。`Series.to_numpy()` 则返回 NumPy 数组，其代价是需要复制、并强制转换数据的值。



 `idxmax()` 与 `idxmin()` 函数计算最大值与最小值对应的索引



`cut() 函数`（以值为依据实现分箱）及 `qcut() 函数`（以样本分位数为依据实现分箱）用于连续值的离散化：