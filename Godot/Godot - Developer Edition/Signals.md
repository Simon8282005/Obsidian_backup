为了要让各种 node 之间进行对话，我们会使用 signal 来通讯，但是一旦 signal 的数量变多，会导致整个 project 的运行速度变慢（lack 想一想当年用 scratch 来做 game 的经历 XDD)

### 1. Avoid Bubbling Signals

说真的，用上 signals 确实很难被追踪，一两个还好，但数量一下多就很麻烦了，更别提像下面这样嵌套了。。。。要找到 Health 工都够多了。。。更别提追踪 signal 了。。。

下面这样的场景就不适合使用 signal，而是应该用 setter and getter

![[Pasted image 20230404120025.png]]

需要释放三次信号才能 update 一次 health，那要是有上百个怪物的 health 需要 update，那游戏可以不用玩了

![[Pasted image 20230404120351.png]]

可以直接让 Health 和 UILifeBar 进行通讯就能解决这个问题了

### 2. AVOID CONNECTIONS WITH MANY STEPS

可以使用物理引擎自带的 signal，比如 `body_entered` 和 `area_entered` 

比起 signal，更好的方式是使用 setter and getter，不仅运行速度比 signal 来的更快，并且也能保持游戏的流畅运行

