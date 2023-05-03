




### dataclasses 数据类
```python
from dataclasses import dataclass

@dataclass
class InventoryItem:
    """Class for keeping track of an item in inventory."""
    name: str
    unit_price: float
    quantity_on_hand: int = 0

    def total_cost(self) -> float:
        return self.unit_price * self.quantity_on_hand

```
示例中使用dataclass的装饰器能够直接定义对应的class 中的参数变量定义
```python
    自动生成对应的__init__()方法，其中参数为name、unit_price、quantity_on_hand
```
