
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

在生成文字的时候，语言模型会根据 _贪心算法_ 或是随机生成下一个候选词，但这个样做的话会导致生成的文本过度重复，很 boring

但在 `top_p` 采样中，预选的字会根据概率排在一起，语言模型会选择该字的概率达到阈值的字作为候选词，并在候选词中选出拥有最高可能性的字或词，这个阈值就是 `top_p`

---

# 基本提示

### Simple prompt

先试试一个简单的提示

```prompt
The sky is
```

语言模型可能会生成以下的句子

```prompt
blue
The sky is blue on a clear day. On a cloudy day, the sky may be gray or white.
```

语言模型生成了一些能与 `the sky is` 作为连接的句子，但要是我们给语言模型一些额外的提示呢

```prompt
Complete the sentence:
The sky is
```

结果：

```prompt
so beautiful today.
```

有了提示，结果有很不一样哦 XDD

但是，ChatGPT 的回答有些吓到我了

![[Pasted image 20230326154850.png]]

ChatGPT 自动帮你把句子接了下去，好家伙

但其他的语言模型生成的句子就有差别了：

![[Pasted image 20230326155102.png]]

Claude 直接显示我不理解你想到的东西是什么 XDD

![[Pasted image 20230326155135.png]]

Dragonfly 效果也很明显，但最后一句 `中文` 我整笑了 XDDD，看来这个语言模型还有待改进

![[Pasted image 20230326155200.png]]

### Prompt Formatting

提示的标准格式为：

```prompt
<Question> 或
<Instruction>
```

并且还有一种格式是 Q&A 形式的:

```prompt
Q: <Question> ?
A: 
```

当我们的提示像以上的形式显示时，被称为 _零樣本提示_ (zero-shot prompting)，意思是语言模型直接对我们的提示做出回答并且不需要我们提供想要实现的任务的例子

根据上面的提示，衍生出了 _少量樣本提示_ (Few-shot prompts) 格式:

```prompt
<Question>?
<Answer>
<Question>?
<Answer>
<Question>?
<Answer>
<Question>?
<Answer>
```

而 Q&A 的格式则是这样的：

```prompt
Q: <Question>?
A: <Answer>
Q: <Question>?
A: <Answer>
Q: <Question>?
A: <Answer>
Q: <Question>?
A:
```

我们给出几个相应的例子让语言模型进行学习，为立刻回答问题

Q&A 格式并不是必须使用的提示格式，而是根据任务的种类复杂度等等，比如我们想让语言模型帮我们分类某些事务:

```prompt
This is awesome! // Positive
This is bad! // Negative
Wow that movie was rad! // Positive
What a horrible show! //
```

输出则是：

`Negative`

对于 Q&A 格式的提示，全部的语言模型都回答的很正确，唯独 `Dragonfly` 语言模型的输出还是需要改进。这种提示格式还是很有效的，但是只能用来处理一些简单的任务

###### ChatGPT

![[Pasted image 20230326160814.png]]

###### Sage

![[Pasted image 20230326160907.png]]

###### Claude

![[Pasted image 20230326160932.png]]

###### Dragonfly

![[Pasted image 20230326161000.png]]


---
# Prompt Elements

在提示里面可以拥有各种各样的元素，比如：

```python
Intruction (指示) - 希望模型能执行特定的任务或者指令
Context (背景) - 可以附上额外资讯或是上下文，让 AI 能更好的做出回答
Input Data (输入) - 输入想要 AI 回答的问题
Output Indicator (输出) - 输出的格式
```

---
# Generally Tips for Designing Prompts

### Start Simple (开始简单)

想学编程时，把一个大任务分成好几个子任务，并且逐一完成，而不是一次过把一项很大很复杂的工作交给模型处理，模型会直接当机啊喂

或是可以从简单的任务开始，慢慢的添加上下文，背景等等已得到最好的结果

### The Intruction (指令)

我们可以使用命令来明确的告诉模型要它帮忙实现那一个目标，比如“写作”，“诗歌”，"分类" 等等

上下文越具体越相互呼应能让模型生成更加准确的结果

```python
### Intruction ###
Translate the text below to Chinese:
Text: "Hello World !"
```

###### ChatGPT

![[Pasted image 20230327132854.png]]

###### Sage

![[Pasted image 20230327132917.png]]

###### Claude 

![[Pasted image 20230327132940.png]]

###### Dragonfly

![[Pasted image 20230327132955.png]]




### Specificity (特异性)

指示写的越详细越细节就越好，尤其关于我们想到的输出结果，但是也不要写太多和任务无关的细节，反而会适得其反

```java
Extract the name of places in the following text  
Desired format:  
Place: <comma_separated_list_of_company_names, places_name>

Input: "Although these developments are encouraging to researchers, much is still a mystery. “We often have a black box between the brain and the effect we see in the periphery,” says Henrique Veiga-Fernandes, a neuroimmunologist at the Champalimaud Centre for the Unknown in Lisbon. “If we want to use it in the therapeutic context, we actually need to understand the mechanism."
```

我去。。。这写的也太精确了吧 XDDD

这次全部的模型生成的结果竟然一模一样？？好家伙

###### ChatGPT

![[Pasted image 20230327133836.png]]

###### Sage

![[Pasted image 20230327133928.png]]

###### Claude

![[Pasted image 20230327133943.png]]

###### Dragonfly

![[Pasted image 20230327133955.png]]

### Avoid Impreciseness (避免不精确)

和模型对话的时候就要当个直男，越直接越好，避免拐弯抹角，要不然谁看的懂啊

```txt
Explain the concept prompt engineering. Keep the explanation short, only a few sentences, and don't be too descriptive.
```

```python
解释一下 Prompt Engineering。让解释保持简短，只有几个句子，同时别太复杂
```

###### ChatGPT

![[Pasted image 20230327134502.png]]

###### Sage

![[Pasted image 20230327134545.png]]

###### Claude

![[Pasted image 20230327134704.png]]

###### Dragonfly

![[Pasted image 20230327134715.png]]


还能写的更详细一些，明确的说明想要多少个句子并且是什么风格

```txt
Use 2-3 sentences to explain the concept of prompt engineering to a high school student.
```

```python
用两到三句的句子为一位高中生解释什么是 Prompt Engineering
```

```python
用两到三句的句子为一位五岁小孩解释什么是 Prompt Engineering
```

###### ChatGPT

![[Pasted image 20230327135011.png]]

和我一开始玩 ChatGPT 的时候一样，回答的真的是连小孩子都看得懂啊

###### Sage

![[Pasted image 20230327135156.png]]

###### Claude

![[Pasted image 20230327135254.png]]

###### Dragonfly

![[Pasted image 20230327135344.png]]


### To do or not to do ? (做还是不做？)

我们在设计 Prompt 时，应该专注在该做什么，而不是画很多的笔墨专注在不该做什么，否则效果可能和我们预想的相差甚远

```javascript
The following is an agent that recommends movies to a customer. DO NOT ASK FOR INTERESTS. DO NOT ASK FOR PERSONAL INFORMATION.Customer: Please recommend a movie based on my interests.
Agent:
```

```javascript
Sure, I can recommend a movie based on your interests. What kind of movie would you like to watch? Do you prefer action, comedy, romance, or something else?
```

```txt
The following is an agent that recommends movies to a customer. The agent is responsible to recommend a movie from the top global trending movies. It should refrain from asking users for their preferences and avoid asking for personal information. If the agent doesn't have a movie to recommend, it should respond "Sorry, couldn't find a movie to recommend today.".Customer: Please recommend a movie based on my interests.Agent:
```

```txt
Sorry, I don't have any information about your interests. However, here's a list of the top global trending movies right now: [list of movies]. I hope you find something you like!
```

