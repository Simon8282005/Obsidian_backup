
# LLM 设定 (Large Language Models) 大型语言模型

### Temperature 温度 

>（啊这个名。。。XDD

在 LLM 中，`temperature` 的值决定了语言模型生成的文本的创意性，如果 `temperature` 的值为 1.0，那么语言模型的生成结果和我们所给的提示非常接近或者完全一直，但如果 `temperature` 为 2.0， 那么生成的结果会和我们给的提示有出入，但也会更有创意，能激发意想不到的脑力激荡

```python
temperature = 1.0  # 我是个老实的孩子
temperature = 2.0  # 我是个有主见有创意的孩子
```

### Top_p 

> （也叫 nucleus sampling）

`top_p` 参数和 `temperature` 差不多，但还是有细节上的区别。`top_p` 的数值通常在 0 - 1.0 之间，但 `temparature` 的数值是能够超过 1.0

在生成文字的时候，语言模型会根据贪心算法或是随机生成下一个候选词，但这个样做的话会导致生成的文本过度重复，很 boring

但

