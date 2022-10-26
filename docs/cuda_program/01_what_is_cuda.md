# CUDA是什么




:earth_asia: **Bilibili视频传送门：**[CUDA编程01：GPU发家史-从游戏到CUDA](https://www.bilibili.com/video/BV1Mb4y1p7BG?share_source=copy_web) :earth_asia:

新手入门CUDA必备知识：

- GPU并行编程的过去和现在

- 编写第一个CUDA程序

这期帮大家梳理GPU并行编程的过去和现在，以及CUDA在其中的作用。

## 1. 早期GPU的应用
显卡最初的目的是让图像能更好的处理和生成、最后输出到显示器上，主要应用于游戏和CG领域。GPU是显卡中最重要的组成部分，常作为显卡的代称。GPU和CPU的差异如下：


| **NO.特性** | **CPU**     | **GPU**     |
|:---------:|:-----------:|:-----------:|
| **定义**    | 中央处理器       | 图形处理单元      |
| **内存消耗**  | 需求大         | 需求小         |
| **速度**    | 速度低         | 速度高         |
| **核心数**   | 拥有少量功能强大的核心 | 拥有大量功能稍弱的核心 |
| **适用领域**  | 适用于串行指令处理   | 适合并行指令处理    |
| **重点**    | 关注低延迟       | 强调高吞吐量      |



<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="01_what_is_cuda_files/gpu_cell.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">早期GPU</div>
</center>


为了将GPU应用于图像处理之外的工作，早期的方法是将任务转换成图像处理的形式，再使用原本用于图像渲染、坐标换算的API完成通用计算。这种方法的学习成本是非常高的，CUDA因此应运而生。

## 2. CUDA的诞生
CUDA：英伟达提出的通用并行计算架构

CUDA和DirectGraphic类似，都是通过调用驱动操纵显卡，不同的是DirectGraphic提供的API主要是和图形有关，而CUDA主要用于支持通用计算。

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="01_what_is_cuda_files/cuda_directgraphic.png" width="40%">
    <br>
</center>

CUDA编程的特点：

- 并行编程

例如两个长度为N的向量相加，对于串行编程，需要循环N次，将这两个向量的元素逐一加和；而CUDA会去开N个线程，同时处理N个元素，也就是并行编程。

- 异构编程

平常的代码都是运行在CPU上的，当我们想要使用GPU的资源时，需要通过特定的语法或函数让GPU分配资源、进行计算，以及将结果拷贝回CPU，这个过程就是异构编程。

