## 总结

此paper是对扩散模型的**综述**，主要介绍了以下几个方面：**时间序列数据和时空序列数据**、**扩散模型的基本原理以及扩散模型的分类**、**扩散模型的应用**

## 时间序列数据和时空数据

**时间序列数据的定义：**

<img width="457" alt="image" src="https://github.com/user-attachments/assets/4efeec15-9244-4394-a90a-b7c107dce1f4">

时间序列包括单变量和多变量：

<img width="243" alt="image" src="https://github.com/user-attachments/assets/0677a9c8-16bb-4b29-ab0e-5b38bd07f317">

**时空数据的定义：**

<img width="512" alt="image" src="https://github.com/user-attachments/assets/6d01ae66-b192-4bb6-8323-57e9a24e718b">

时空数据包括STG和STT：

<img width="448" alt="image" src="https://github.com/user-attachments/assets/16d7ddb8-1dc7-462f-8799-2826d73dc1df">

其中STG又包括domain-oriented和domain-agnostic：

<img width="447" alt="image" src="https://github.com/user-attachments/assets/95895c13-10d7-4e6c-ad23-baaa6aebdf84">

其中domain-oriented侧重于特定领域的学习，而domain-agnostic侧重于在不同领域学习的迁移

## 扩散模型

### 1.Denoised Diffusion Probabilistic Models (DDPMs)

**Diffusion Process:**

通过下面的过程对原始数据进行K步加噪处理： 
  
<img width="853" alt="image" src="https://github.com/user-attachments/assets/2c153f61-57ca-4a91-883b-c5cdb56781a5">  
  
则第k步的数据满足的分布如下：  
  
<img width="515" alt="image" src="https://github.com/user-attachments/assets/dc92e4d1-f881-4e22-a062-a46b83ea6ed4">

根据高斯分布的性质，可以从第0步直接得到第k步的分布：  
  
<img width="520" alt="image" src="https://github.com/user-attachments/assets/ef9fe7b2-f6d3-441b-a180-196be6a6bb5a">

**Denoising Process:**

由贝叶斯公式可以得到：

<img width="600" alt="image" src="https://github.com/user-attachments/assets/e7613937-9acb-42b1-9935-41a5ad597b93">

将具体数值带入，可以得到：

<img width="821" alt="image" src="https://github.com/user-attachments/assets/af959d4f-d25e-4e57-8f8f-30ad7eef8231">

显然此时只要得到噪声ε，即可一步步反推得到x<sub>0</sub>，因此可以借助神经网络完成对其的估计：

<img width="432" alt="image" src="https://github.com/user-attachments/assets/4aa6698d-dfc4-4348-ae7b-5d2bf03206f6">

其中神经网络的Loss Function如下：

<img width="389" alt="image" src="https://github.com/user-attachments/assets/560e9af1-b91c-4ba0-94a4-c34d0c46a3ba">

### 2.Score SDE Formulation

与DDPMs不同，SDE将DDPMs的离散情况推广到连续

**Forward Process：**

<img width="388" alt="image" src="https://github.com/user-attachments/assets/6cb0c45b-6262-4f13-8368-3d9cf15f0652">

**Reverse Process：**

<img width="390" alt="image" src="https://github.com/user-attachments/assets/2bf66d95-13b9-4d64-9826-41fe517c2beb">

其中神经网络的Loss Function如下：

<img width="390" alt="image" src="https://github.com/user-attachments/assets/99cae6e5-06fa-4af3-9321-3e3691e6288b">

### Conditional Diffusion Model

Conditional Diffusion Model的定义：

<img width="509" alt="image" src="https://github.com/user-attachments/assets/d7175d5a-86d1-406c-ada9-16de5664207b">

Conditional Diffusion Model的适用范围：

由于其高度的特定性以及输出可控性，可以用于特定的场景

### 常见的生成模型

<img width="462" alt="image" src="https://github.com/user-attachments/assets/c36d7a3f-30a3-459a-b2fc-14eaec0e711a">

## 扩散模型的应用领域

+ Forecasting

+ Generation

+ Imputation

+ Anomaly Detection

## 参考文献：[bilibili](https://www.bilibili.com/video/BV1tz4y1h7q1/?spm_id_from=333.337.search-card.all.click&vd_source=887e79a2964e5ce84cbcf68e50febd27)

