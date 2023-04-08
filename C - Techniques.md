# Zero - shot prompt

zero - shot 指的就是没有任何的提示，就让 LLMs 来执行任务，现在的 LLMs 经过很多次的迭代已经能够很好的处理这一类型的任务了（当然如果处理不了还是需要给上几条提示的）

```txt
Classify the text into neutral, negative or positive.
Text: I think the vacation is okay.
Sentiment:
```

Output:

```txt
neutral
```

# Few - shot prompt (少量樣本提示)

为了让 LLMs 能处理更加复杂的任务，出现了 Few - shot prompt 的命令，根据任务的复杂程度也能给与不同行数的的提示(3 行，5行，甚至更多)

下面的例子展示了如何使用 Few - shot prompt 来让 LLMs 正确的在句子中使用一个新的单词：

```txt
A "whatpu" is a small, furry animal native to Tanzania. An example of a sentence that usesthe word whatpu is:
We were traveling in Africa and we saw these very cute whatpus.

To do a "farduddle" means to jump up and down really fast. An example of a sentence that usesthe word farduddle is:
```

Output:

```
When we won the game, we all started to farduddle in celebration.
```


### 统一标签
还有一种就是标签了，还记得之前学的让 LLMs 判断那一个句子是 positive，negative 和 neutral 的例子吗：

```
This is awesome! // Negative
This is bad! // Positive
Wow that movie was rad! // Positive
What a horrible show! //  

Output = Negative
```

上面的 `Negative`, `Positive` 和 `neutral` 就是所谓的标签了，但是不一定全部的标签都要那么统一，但最重要的是有标签，有了标签，能让 LLMs 输出的结果产生很大的改变

### 随机标签

```
Positive This is awesome!
This is bad! Negative
Wow that movie was rad!Positive
What a horrible show! --

Output = Negative
```


### Limitations of Few-shot Prompting

但是 Few - shot prompt 还是会有所限制的，不能完美的应对所有的难题

```
The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.
A:

	Output = Yes, the odd numbers in this group add up to 107, which is an even number.
```

看来需要给 LLMs 更多的例子了。。

```
The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
A: The answer is False.

The odd numbers in this group add up to an even number: 17, 10, 19, 4, 8, 12, 24.
A: The answer is True.

The odd numbers in this group add up to an even number: 16, 11, 14, 4, 8, 13, 24.
A: The answer is True.

The odd numbers in this group add up to an even number: 17, 9, 10, 12, 13, 4, 2.
A: The answer is False.

The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.
A: The answer is True.
```

emm 看起来答案还是错的呢，是时候需要用另外一种更先进的方法了，那就是 CoT Chain - of - Thought (思维链)

不过经过测试，ChatGPT，Claude 和 Dragonfly 都给出了正确的答案，但是唯独 Sage 给出了错的答案呢。。。

# Chain of Thought

可以理解成在再给出提示的命令时也顺便把详细的解答过程写出来，让模型自行学习

![[Pasted image 20230408084438.png]]

### Sage

终于答对了 XDDD

![[Pasted image 20230408085212.png]]

## zero-shot COT Prompting

最新的方法，是让模型来一步一步的写出解答的过程

![[Pasted image 20230408085529.png]]

![[Pasted image 20230408085540.png]]

注意看，在最后一行时加入了 `Let's think step by step` 的句子

### ChatGPT

好家伙，现在的模型都已经能够自己写出详细的过程了吗 XDD

![[Pasted image 20230408085823.png]]

### Claude

![[Pasted image 20230408085929.png]]

### Sage

![[Pasted image 20230408085949.png]]

### Dragonfly

Dragonfly 还是错了呢。。。

![[Pasted image 20230408090000.png]]

---
# Self-Consistency 自我一致性

我的理解是，和 Few - shot prompt 是差不多的，提供的例子也有一致性

### Claude

错了呢。。

![[Pasted image 20230408090823.png]]

### Dragonfly

也是错了呢。。。

![[Pasted image 20230408090852.png]]

 