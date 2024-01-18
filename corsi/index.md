# CORSI 实验初步 demo 开发

## 2024-01-18

### 后续设想构思
* 使用一个 difficulty 变量来控制整个程序的步进。可以先从 staircase 模式做起，先暂时不考虑自适应。
* 考虑如何编写自定义函数与回调，以及如何根据不同的参数触发不同的 trial。需要研究一下 timeline。

## 2024-01-17

### 已完成部分
完成了一个初步 trial 的构建（见[此 repo](https://github.com/Midnight-Yu/jspsych-adaptive-corsi-demo)）。
* jsPsych的默认框架为“1 trial, 1 response”。这种情况下要么硬堆trial数量（吃撑了），要么就得自行开发插件（comment by [Shaobin-Jiang](https://github.com/Shaobin-Jiang)）。
* 确实是不会手写 Javascript，好在找到了一个现成的CORSI任务插件——[corsi-blocks](https://github.com/jspsych/jspsych-contrib/tree/main/packages/plugin-corsi-blocks)。是一款社区插件。
* 用这个插件现场写了一个 trial 出来，看着能跑，单个 trial 目前很成功。
* 对页面 CSS 做了一些调整和规划，复用了之前实验使用的 CSS 框架。
* 还真让我把 randomization 做出来了，虽然比较粗糙，reverse 的问题也解决了。
  * 但是如何批量生成是个问题，现在是 trial by trial 的，考虑到这是个 trial 数量都不固定的任务，完全动态的生成是很有必要的。
* 做了下 timeline 和传参，目前的结果看上去一切都好，作为一个 demo 它很成功。


### 下一步做什么？
* ~~刺激和反应的 randomization。先搞定随机化再说自适应的问题。~~
  * ~~有个问题是，它的结构是把 display 和 input 分成两个 trial。考虑到任务的需求是反向，我就要分两次传参数。问题更大的是，好像 jsPsych 是一次性初始化所有 trial？不确定这里能不能写成动态的。~~
* ~~完全自动化的随机列表生成，为下一步出自适应做铺垫。~~
* 构建自适应框架，感觉会需要写很多个 timeline。
  * 需要分阶段分大小设置不同的网格
* 自行构建一个对应的插件
  * 这个地方只支持方块。考虑到图形化的需求，那必然是要重写这个插件的一部分逻辑的。还是得手写 JS，哈哈。
