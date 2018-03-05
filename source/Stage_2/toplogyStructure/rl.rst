增强学习
========


对于简单的分类的问题，我们可以直接用DL这种监督学习。 对于没有办法直接产生label,或者本身的label就像难以有结构化的描述时怎么办呢。 
一个办法，那就是增强学习，传统的增强学习就是State,Action,reward之间的转换.

#. 原来的label变成了 State, 是可以用一堆向量来表示。
#. 原来的forward 就变成长了现在 Action.
#. 原来的loss函数，现在变成reward 函数。 

相当于这些通用化之后就是capsule 网络。 

这样离DL的核心更进了一步。 DL可以的输出去掉active函数就是向量或者feature. 
同时DL是可以模拟任何函数，而函数的本质就是映射，所以DL也就是拟合各种映应的。
而传统 Q,A 组合，本身也是会产生组合爆炸的。只能针对比较小的问题。

也就是任何一个 A->B, y=f(x), 任何关系(A,B) 我们可以用 :math:`f(\thea,A,B)` 来模拟。

而DQL就是利用DL 通过 feature + 参数来拟合，Value函数与Q函数。这也正是AlphaGO所采用的方法。

AutoML则是进一步，包括超参数也变成了网络的一部分，也就是现在AlphaZero,AutoML的功能。



.. figure:: /Stage_2/rl/rl.png

本质就是一种试错学习法。当然可以是单步的试错，也可以多步回合制的试错。
介于监督学习与非监督学习之间。

.. figure::  /Stage_2/rl/RL4.png


一种是对环境无知状态的学习，也就是瞎摸形式，主要依赖环境的反馈来学习，
另一种有模型的学习，这个有点偏向迁移学习。

各种方法的不同，主要是更新机制的不同。对于传统的神经网络，所有的反馈是需要我们来设计的，
而我们添加环境，这样环境会直接给出一些反馈。而不是再需要人为的设计反馈。

当然学习方法，也有offline/online,对于能够实时cost计算当然online可能会快一些。
对于一些需要多步的，offline,就可以会方便。这个就像敏捷开发，每一次选择一个模块集来实现。
然后选择最好的。然后再决定一步的开发。



Q-Learning
==========

.. figure:: /Stage_2/rl/q4.png

Q-Learning 

基本组成:
--------

#. Agent
#. State S
#. Environment 
#. Reward
#. action A

传统的action,reword模式解空间太大，现在都是采用增强学习模式，每一个部分都采用DL来实现。

而alphaGo就是采用的增强学习模式。而openai,elf,这些库都是用来研究RL的平台。

难点是如何定义reword,是单步的，一步回合制的。回合制是需要多步回逆的。也可以说是A*算法的，DL化。 


.. math:: 
   
   Q (state， action) = R(state， action) + gamma * Max[Q(next state， all actions)]


简单的说那就是模仿学习。关键是如何正确的给出实时的反馈。 因为最简单的失败可能需要多步之后才能给出，这样就需要马尔科夫链之类的反馈机制。

主要利用应用领域:


#. 游戏理论与多主体交互
#. 机器人
#. 电脑网络
#. 车载导航
#. 医学
#. 工业物流


马尔科夫决策过程
================

#. 状态集  S
#. 协作集 A
#. 奖励函数 R
#. 策略 :math:`\pi`
#. 价值,V 


基本理论
========

#. DP 动态编程
#. Monte Carlo 蒙特卡洛方法
#. Temproal-Difference 时分法
#. Q-Learning off-policy TD
#. Sarsa on-policy TD
#. R-Learning
#. Policy Search/Gradient
#. Hierarchical RL


Actor-Critic的方法，是采用的两头凑的方法。