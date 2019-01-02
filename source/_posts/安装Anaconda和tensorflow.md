---
title: 安装Anaconda和tensorflow
date: 2019-01-02 13:51:54
tags:
---

## 安装Anaconda和tensorflow
> 日期：2019-01-01

### Anaconda介绍
Anaconda指的是一个开源的Python发行版本，其包含了conda、Python等180多个科学包及其依赖项。

### Anaconda安装步骤
1. 前往官网，下载安装包，这里我们选的是图形化的安装方式，选择Python3.x版本，下载了Anaconda3.
2. 点击安装包完成安装。
3. 安装完成后，在mac的Launchpad可以找到“Anaconda-Navigator”，点击可以打开。

### 验证安装
1. 安装完成后，anaconda在`~/anaconda3`目录下，将`export PATH=$PATH:/Users/xxxx/anaconda3/bin`加入环境。（这里是在Mac Os下进行安装的）
2. `conda --version`可以显示conda版本号，表明安装成功。

### 建立tensorflow环境
`conda create -n tensorflow python=3.7`

### 设置国内镜像
设置为清华镜像可以加快速度。
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/  
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/  
conda config --set show_channel_urls yes
```
### 安装TensorFlow
```
// 激活环境
source activate tensorflow
// 安装tensorflow
conda install tensorflow
// 关闭环境
source deactivate
```

### 测试是否安装成功
```
import tensorflow as tf
hello = tf.constant('Hello,tensorflow')
sess = tf.Session()
print(sess.run(hello))

```
以上代码可能运行报错“Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2”，意思是“你的CPU支持AVX扩展，但是你编译安装的TensorFlow版本不支持该特性。”

> AVX是一个x86指令集体系结构的扩展，可以加速线性代数计算。

原因是一般tensorflow是用GPU运算的，如果想单纯用CPU，而你的CPU又支持AVX拓展，可以使用专门针对CPU优化的支持AVX的tensorflow。默认下载安装的tensorflow不支持AVX，所以我们忽略这个警告就行。

在代码前面加入以下代码，即可忽略。
```
import os 
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2' 
// 默认级别为1，显示所有信息。
// 级别2显示warning和error，级别3只显示error
```

### 参考文章

1. https://zhuanlan.zhihu.com/p/32925500
2. https://blog.csdn.net/hq86937375/article/details/79696023
3. https://www.jianshu.com/p/aaf216f4152c