### 1. Paper title: Automatic differentiation in geophysical inverse problems, Geophysics, 2007
![image](https://github.com/user-attachments/assets/5c53ebfb-25ab-43aa-9d5f-3286d7989b52)

### 2. Problem to solve:

从多个角度表示梯度/导数计算的重要性，例如正向建模结果相对于输入变量的灵敏性分析；地球物理数据的反演优化问题(特别是当未知参数较大且关系非线性时，梯度计算难度较大)；人工推导时间成本和工程代码编写以及debug的成本较大，灵活性较差(条件变化需要重新进行解析式或数值式的推导)，此外数值解还需要平衡准确性和近似网格大小。从这三个角度得到一个理想的微分方法能够实现：

1. 计算精确的梯度
2. 与输入变量相独立，降低计算负担
3. 降低人工推导和计算的成本
   
### 3. Major contribution:
自动微分技术可以满足上面三个要求，但是其在地球科学中的应用影响力较低。本文的目的是将自动微分技术进一步在地球科学研究社区中推广，简要阐述了该方法的基本理论并列举了三个地球科学领域问题的自动微分实践案例

### 4. Experiment results:



### 5. Lessons learnt:

