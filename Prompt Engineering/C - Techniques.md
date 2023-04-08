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

> 将思考和推理的过程也教给模型，帮助模型提高其推理能力
> 
> 该方法在数学推理测试集GSM8K上，将指标提升到了60.1%左右。

![[Pasted image 20230408084438.png]]

### Sage

终于答对了 XDDD

![[Pasted image 20230408085212.png]]

## zero-shot COT Prompting

最新的方法，是让模型来一步一步的写出解答的过程

![[Pasted image 20230408085529.png]]

![[Pasted image 20230408085540.png]]

注意看，在最后一行时加入了 `Let's think step by step` 的句子，模型会输出思考的过程

emmm。。。看了知乎大神的文章后发现，这个方法其实有分成两步：

### 第一步

加上一句 `Let's think stepj by step`，已让模型输出思考推理的过程，像这样：

```text
---模型的输入：---
Q: Joe平均每分钟出拳25次。一场战斗持续5轮，每轮3分钟。他打了多少拳？
A: 让我们一步一步地思考。

---模型的输出：---
一分钟内，乔出拳25次。
三分钟内，乔出拳3*25=75次。
在五个回合中，乔出拳5*75=375次。
```

### 第二步

在第一步模型输出的基础上，我们像让模型的答案为数字而已，因此需要加上 `So, the answer (arabic number) is` ...

模型最后的答案将会是 375

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

我的理解是，和 Few - shot prompt 是差不多的，提供的例子也有一致性 (啊这。。。理解有误呢 XDD)

> 该方法主要利用的是模型每次生成的结果都不是完全相同的这个性质。
> 
> CoT prompting 是预测出一个结果就直接使用这个结果；而 self-consistency 就是先用 CoT prompting 方法预测出多个结果，然后选择预测出频次最多的那个结果

该方法在数学推理测试集GSM8K上，将指标提升到了74.4%左右。

![[Pasted image 20230408103255.png]]

> CoT prompting 是预测出一个结果就直接使用这个结果；而 self-consistency 就是先用 CoT prompting 方法预测出多个结果，然后选择预测出频次最多的那个结果。(**使用产生的结果选择最一致的答案**)

### Claude

错了呢。。

![[Pasted image 20230408090823.png]]

### Dragonfly

也是错了呢。。。

![[Pasted image 20230408090852.png]]

### 例子

```text
Q: There are 15 trees in the grove. Grove workers will plant trees in the grove today. After they are done,there will be 21 trees. How many trees did the grove workers plant today?

A: We start with 15 trees. Later we have 21 trees. The difference must be the number of trees they planted. So, they must have planted 21 - 15 = 6 trees. The answer is 6.

Q: If there are 3 cars in the parking lot and 2 more cars arrive, how many cars are in the parking lot?

A: There are 3 cars in the parking lot already. 2 more arrive. Now there are 3 + 2 = 5 cars. The answer is 5.

Q: Leah had 32 chocolates and her sister had 42. If they ate 35, how many pieces do they have left in total?

A: Leah had 32 chocolates and Leah’s sister had 42. That means there were originally 32 + 42 = 74 chocolates. 35 have been eaten. So in total they still have 74 - 35 = 39 chocolates. The answer is 39.

Q: Jason had 20 lollipops. He gave Denny some lollipops. Now Jason has 12 lollipops. How many lollipops did Jason give to Denny?

A: Jason had 20 lollipops. Since he only has 12 now, he must have given the rest to Denny. The number of lollipops he has given to Denny must have been 20 - 12 = 8 lollipops. The answer is 8.

Q: Shawn has five toys. For Christmas, he got two toys each from his mom and dad. How many toys does he have now?

A: He has 5 toys. He got 2 from mom, so after that he has 5 + 2 = 7 toys. Then he got 2 more from dad, so in total he has 7 + 2 = 9 toys. The answer is 9.

Q: There were nine computers in the server room. Five more computers were installed each day, from monday to thursday. How many computers are now in the server room?

A: There are 4 days from monday to thursday. 5 computers were added each day. That means in total 4 * 5 = 20 computers were added. There were 9 computers in the beginning, so now there are 9 + 20 = 29 computers. The answer is 29.

Q: Michael had 58 golf balls. On tuesday, he lost 23 golf balls. On wednesday, he lost 2 more. How many golf balls did he have at the end of wednesday?

A: Michael initially had 58 balls. He lost 23 on Tuesday, so after that he has 58 - 23 = 35 balls. On Wednesday he lost 2 more so now he has 35 - 2 = 33 balls. The answer is 33.

Q: Olivia has $23. She bought five bagels for $3 each. How much money does she have left?

A: She bought 5 bagels for $3 each. This means she spent 5 * 3 = $<<5*3=15>>15. She started with $23 and spent $15, so she has $23 - $15 = $<<23-15=8>>8 left. The answer is $8. 

Q: When I was 6 my sister was half my age. Now I’m 70 how old is my sister?

A: 
```

`When you were 6, your sister was half your age, so she was 6 / 2 = 3 years old. Now, you are 70 years old, and your sister is 70 - (6 - 3) = 67 years old. The answer is 67.`

原理是从多个结果里拿出最具一致性的答案，不过这个例子很长啊 XDD

---
# 產生知識提示

![[Pasted image 20230408105056.png]]

> 生成用作提示的知识

`高尔夫的一部分是试图获得比其他人更高的得分总数。是或不是？`

`是的，高尔夫的一部分是试图获得比其他人更高的得分总数。`

(虽然 ChatGPT 已经答对了这一题。。。XDD 但还是要了解一下这个的原理的，因为不是所有的模型都能答对呢。。）

那就需要给予模型一些知识了 嘛哩嘛哩哄。。。（施法中

```text
Input: Greece is larger than mexico.
Knowledge: Greece is approximately 131,957 sq km, while Mexico is approximately 1,964,375 sq km, making Mexico 1,389% larger than Greece.

Input: Glasses always fog up.
Knowledge: Condensation occurs on eyeglass lenses when water vapor from your sweat, breath, and ambient humidity lands on a cold surface, cools, and then changes into tiny drops of liquid, forming a film that you see as fog. Your lenses will be relatively cool compared to your breath, especially when the outside air is cold.

Input: A fish is capable of thinking.
Knowledge: Fish are more intelligent than they appear. In many areas, such as memory, their cognitive powers match or exceed those of ’higher’ vertebrates including non-human primates. Fish’s long-term memories help them keep track of complex social relationships.

Input: A common effect of smoking lots of cigarettes in one’s lifetime is a higher than normal chance of getting lung cancer.
Knowledge: Those who consistently averaged less than one cigarette per day over their lifetime had nine times the risk of dying from lung cancer than never smokers. Among people who smoked between one and 10 cigarettes per day, the risk of dying from lung cancer was nearly 12 times higher than that of never smokers.

Input: A rock is the same size as a pebble.
Knowledge: A pebble is a clast of rock with a particle size of 4 to 64 millimetres based on the Udden-Wentworth scale of sedimentology. Pebbles are generally considered larger than granules (2 to 4 millimetres diameter) and smaller than cobbles (64 to 256 millimetres diameter).

Input: Part of golf is trying to get a higher point total than others.
Knowledge: This statement is incorrect. In golf, the objective is to complete a course consisting of 18 holes in as few strokes as possible. The player with the lowest number of strokes at the end of the round is the winner. There is no point system in golf and getting a higher score than others is not the goal.
```

太长？那就看中文版本的 XDD

```text
Input: Greece is larger than mexico.
Knowledge: 希腊的面积约为131,957平方公里，而墨西哥的面积约为1,964,375平方公里，使墨西哥比希腊大了1,389％。

Input: Glasses always fog up.
Knowledge: 当汗水、呼吸和周围湿度中的水蒸气落在冷表面上时，会发生凝结，冷却并变成微小的液滴，形成雾。你的镜片相对于你的呼吸会比较冷，特别是在外部空气寒冷时。

Input: A fish is capable of thinking.
Knowledge: 鱼比它们看起来更聪明。在许多领域，如记忆力，它们的认知能力与或超过其他“高级”脊椎动物，包括非人类灵长类动物。鱼的长期记忆帮助它们追踪复杂的社交关系。

Input: A common effect of smoking lots of cigarettes in one’s lifetime is a higher than normal chance of getting lung cancer.
Knowledge: 那些在一生中平均每天吸烟不到一支的人，患肺癌的风险比从未吸烟的人高九倍。在每天吸烟一到十支的人中，患肺癌的风险几乎比从未吸烟的人高12倍。

Input: A rock is the same size as a pebble.
Knowledge: 碎石是指根据沉积学的Udden-Wentworth比例尺，粒径为4至64毫米的岩石碎屑。 碎石通常被认为比颗粒（直径2至4毫米）大，比卵石（直径64至256毫米）小。

Input: Part of golf is trying to get a higher point total than others.
Knowledge: 这句话是不正确的。在高尔夫球中，目标是在18个球洞的规定范围内尽可能少地挥杆。在回合结束时，杆数最少的球员获胜。高尔夫球中没有积分制度，得到比其他人更高的分数不是目标。
```

### 其他的例子

```
问题：高尔夫球的一部分是试图比其他人获得更高的分数。是或否？  
  
知识：高尔夫球的目标是以最少的杆数打完一组洞。一般一场高尔夫球赛包括18个洞。每个洞在标准高尔夫球场上打一次。每一杆都算一分，总杆数用于确定比赛的获胜者。  
  
解释和答案：
```

```
否。高尔夫球的目标是以最少的杆数打完一组洞，每一杆都算一分，总杆数用于确定比赛的获胜者。因此，高尔夫球的一部分是试图比其他人获得更低的分数。
```

第二次回答的时候没有那么自信了 XDD

```
问题：高尔夫球的一部分是试图比其他人获得更高的分数。是或否？  
  
知识：高尔夫球是一项需要精密球杆技术的运动，参赛选手（或高尔夫球手）使用多种类型的球杆将球打进球场上的一系列洞中，以最少的杆数完成比赛。目标是用最少的杆数完成比赛，得分是通过计算每个洞上的杆数总和得出的。得分最低的球员获胜。  
  
解释和答案：
```

```
回答：否。高尔夫球的目标是用最少的杆数完成比赛，得分是通过计算每个洞上的杆数总和得出的。因此，高尔夫球的一部分是试图比其他人获得更低的分数，得分最低的球员获胜
```

---
# Automatic Prompt Engineer (APE) 自动优化提示

这里先挖一个坑，之后再去补回来 XDDD 貌似有难度呢

[Automatic Prompt Engineer APE](https://promptingguide.azurewebsites.net/techniques/ape)


---
# Active Prompt

![[Pasted image 20230408111849.png]]

> 以下是方法的示意圖。第一步是使用LLM查詢帶有或不帶有一些CoT示範。對於一組訓練問題，產生_k_個可能的答案。基於_k_個答案計算不確定度度量（使用不一致性 数字越大越不确定）。選擇最不確定的問題由人類進行註釋。然後使用新的註釋示範來推斷每個問題。

因为 CoT 的方法以来人工给与的例子，但这些例子并不一定是最有效的，所以就出现了 Active Prompt 这个方法

---
# Directional Stimulus Prompting方向性刺激提示

![[Pasted image 20230408112716.png]]

注意看左右两边的例子，左边的例子有一句：`Hint: ...` 的字眼，就像 Sej 里的 soalan stimulus，添加 Hint 句子能让语言模型更清楚的知道你想要的输出和关键字（也包括格式）从而输出更准确的答案

好家伙，真的很神奇

# ReACT

> 其中LLMs以交替的方式產生推理追蹤和任務特定的操作。產生推理追蹤使模型能夠誘導、追蹤和更新行動計劃，甚至處理異常情況。

![[Pasted image 20230408113033.png]]

---
# Multimodal CoT

> 傳統的CoT側重於語言模態。相比之下，多模態CoT將文字和視覺融入到一個兩階段框架中。第一步涉及基於多模態資訊的理由產生。接下來是第二階段的答案推理，利用產生的理由進行推理。

![[Pasted image 20230408113543.png]]

---
# GraphPrompts

挖坑，待补 XDD

