---
layout: post
title: 数据挖掘方法之一：主成份分析
description: 数据挖掘专题之一
category: blog
---

##一 概念

主成分分析（principle componentsanalysis,PCA）是指将多个变量通过线性组合，选出较少个数的重要变量集合来描述相关结构的额一种统计分析方法，这些线性组合被称为“成分”。由m个变量组成的数据集的总变异，可以由k个线性组合变量组成的子集来标示（k<m）。这意味着k个变量与原来的变量反应了几乎同样多的信息  

##二 步骤

<ol>
<li>原始指标数据的标准化采集p维随机向量
<img src="/images/blog/PCA1.png">构造样本阵，对样本元素进行如下标准化变换
<img src="/images/blog/PCA2.png"> 得标准化矩阵Z。<br></li>
<li>对标准化矩阵Z求相关系数矩阵<img src="/images/blog/PCA3.png"> </li>
<li>求解样本相关矩阵R的特征方程<img src="/images/blog/PCA4.png">确定n的值，使信息的利用率达85%以上。<img src="/images/blog/PCA5.png"><br></li>
<li>将标准化后的指标变量转换成主成分。<img src="/images/blog/PCA6.png"><br></li>
<li>对n个主成份进行综合评价。对n个主成份进行加权求和，即得最终评价值，权数为每个主成份的方差贡献率。</li>
</ol>

##三 关键性结论

以下结论对主成份分析非常重要<br>
<ol>
<li>结论1：标准化数据集州农工的总体变动性等于所有Z向量方差之和，等于每个成分方差之和，等于特征权值之和，等于变量的个数。即<br><img src="/images/blog/PCA7.png"></li>
<li>结论2：给定成分与给定变量间的偏相关性是特征向量与特征值的函数。具体来说<br><img src="/images/blog/PCA8.png">是相关系数矩阵p的<font color="gray">特征值-特征向量</font>对，并且偏相关系数包括了所有变量之间的影响。</li>
<li>结论3：Z中第i个主成份解释了变量的总体变异的百分比，等于第i个特征根与变量个数之间的比率<img src="/images/blog/PCA9.png"></li>
</ol>

##四 应用于实际数据  

   <img src="/images/blog/PCA10.png">
<ul>
    <li>>1.使用上图的均值和标准差对变量进行标准化，得到Z向量。</li>
    <li>>2.研究下图中变量矩阵图以检验变量间是否存在相关性。</li>
</ul>
可以看到 总房数、卧室数、人口数和家庭数之间表现出正相关性，西经和北纬表现出负相关性。再来观察变量的相关性矩阵：
![相关性矩阵](/images/blog/PCA4.jpg)

 矩阵图和相关矩阵式常用的两种方法，用来观察预测变量之间的相关性结构。  
如果完成一次住房价预测的多元回归分析，但不考虑数据集中的多重共线性将导致回归结果非常不稳定，预测值的微小变化将会导致回归系数的极大变化，而得不到任何结论。此时需要用主成分分析，其可以通过相关化结构，确定相关变量的基本组成部分
   <li>>3. 采用主成分分析对房屋数据集进行分析，该要素矩阵（下图）中每个栏目代表成分Yi=e'Z中的一项。栏目中元素为成分的权重，代表了变量与成分的偏相关。结论2 表明这些成分的权重等于Corr(Yi,Zi),成分涉及第i个特征向量和特征值
    </li>
   ![成分矩阵2](/images/blog/PCA5.jpg)
   <li>>4. 结论3表明，Z的总变异种第i个主成分所占的比例是ri/m(其中ri是特征值)，即第i个特征值与变量数的比例。由下图可以看出，第一特征值是 3.091,因为有8个预测变量，第一主成分解释 3.091/8=48.767%的变异。
   </li>  
![12](/images/blog/PCA6.jpg)
   