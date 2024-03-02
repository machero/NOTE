### 梯度累加（gradient accumulation）

1. 将几个step的梯度进行累加，从某种意义上来说能够实现大的batch_size的效果，从某种意义上来说希望在较小的显存上实现较大的batch_size

2. 在多任务中进行梯度累加，可以减小对应的显存的使用。多个任务中由于计算多个loss 可能需要维护多张计算图，利用梯度累加能够释放一张计算图的梯度值，使得模型中总是保证一张计算图的内存。因此使用梯度累加时可以实现加速效果











#### 分布式训练

`nn.DataParallel`：用于

`nn.distributedataparallel`

