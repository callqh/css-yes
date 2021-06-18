# line-height 继承问题

- 1.2/20px,这些固定数值都是直接继承,然后根据自身的 font-size 进行计算确定的
- **200%,像这种百分比的,是根据父级的 font-size\*line-height 计算后再进行继承的**
