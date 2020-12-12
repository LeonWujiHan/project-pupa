---
title: "角动量总结"
date: 2020-12-13T01:29:23+08:00
description: "韩无极: 作为示例, 将上学期整合量子力学与分子光谱的笔记贴出, 主要是赵新生老师《中级物理化学》教材的总结."
draft: false
---

## 角动量的本征态与本征值
定义三维物理空间中的矢量算符$\hat{\boldsymbol{J}}=\hat{J}\_x\boldsymbol{e}\_1+\hat{J}\_y\boldsymbol{e}\_2+\hat{J}\_z\boldsymbol{e}\_3$
的三个分量$\hat{J}\_x$,$\hat{J}\_y$,$\hat{J}\_z$ 满足如下对易关系,
称为角动量算符
$$\left[\hat{J}\_x,\hat{J}\_y\right]=\mathrm{i}\hbar\hat{J}\_z,\ \ \left[\hat{J}\_y,\hat{J}\_z\right]=\mathrm{i}\hbar\hat{J}\_x,\ \ \left[\hat{J}\_z,\hat{J}\_x\right]=\mathrm{i}\hbar\hat{J}\_y
    .$$ 或写为
$$\left[\hat{J}\_i,\hat{J}\_j\right]=\mathrm{i}\hbar\varepsilon\_{ijk}\hat{J}\_k
    .$$ 其中$$\varepsilon\_{ijk}=
    \begin{cases}
        \left(-\right)^{N\left(\sigma\right)},\ \ \left(i\neq j\right)\cap \left(j\neq k\right)\cap \left(k\neq i\right)\\\\
        0,\ \ \left(i=j\right)\cup \left(j=k\right)\cup \left(k= i\right)
    \end{cases}
    .$$ $\sigma$ 为$ijk$ 的置换, $N\left(\sigma\right)$ 为置换的逆序数.
进一步定义角动量平方算符 $$\hat{J}^2=\hat{J}\_x^2+\hat{J}\_y^2+\hat{J}\_z^2
    .$$ 考虑$\hat{J}^2$ 与$\hat{J}\_x$ 的对易关系有 $$\begin{aligned}
        \left[\hat{J}^2,\hat{J}\_x\right]&= \left[\hat{J}\_y^2,\hat{J}\_x\right]+\left[\hat{J}\_z^2,\hat{J}\_x\right] \\\\
        &= \hat{J}\_y^2\hat{J}\_x-\hat{J}\_x\hat{J}\_y^2+\hat{J}\_z^2\hat{J}\_x-\hat{J}\_x\hat{J}\_z^2 \\\\
        &= \hat{J}\_y\left(\hat{J}\_y\hat{J}\_x\right)-\left(\hat{J}\_x\hat{J}\_y\right)\hat{J}\_y +\hat{J}\_z^2\hat{J}\_x-\hat{J}\_x\hat{J}\_z^2 \\\\
        &= \hat{J}\_y\hat{J}\_x\hat{J}\_y-\mathrm{i}\hbar\hat{J}\_y\hat{J}\_z-\hat{J}\_y\hat{J}\_x\hat{J}\_y-\mathrm{i}\hbar\hat{J}\_z\hat{J}\_y+\hat{J}\_z^2\hat{J}\_x-\hat{J}\_x\hat{J}\_z^2 \\\\
        &= -\mathrm{i}\hbar\hat{J}\_y\hat{J}\_z-\mathrm{i}\hbar\hat{J}\_z\hat{J}\_y+\mathrm{i}\hbar\hat{J}\_z\hat{J}\_y+\mathrm{i}\hbar\hat{J}\_y\hat{J}\_z \\\\
        &=0
    .\end{aligned}$$ 类似地可得$\left[\hat{J}^2,\hat{J}\_y\right]=0$,
$\left[\hat{J}^2,\hat{J}\_z\right]=0$. 于是有
$$\left[\hat{J}^2,\hat{J}\_i\right]=0
    .$$ 考虑$\hat{J}^2$
与角动量任意分量(下文讨论$\hat{J}\_z$)的共同本征矢$\left|ab\right>$, 满足
$$\hat{J}^2\left|ab\right>=a\left|ab\right>,\ \ \hat{J}\_z\left|ab\right>=b \left|ab\right>
    .$$ 其中$a$ 由于$\hat{J}^2$ 对于每个分量作用两次, 一定为正实数.
又由于
$$\left(\hat{J}\_x^2+\hat{J}\_y^2\right)\left|ab\right>=\left(\hat{J}^2-\hat{J}\_z^2\right)\left|ab\right>=\left(a-b^2\right)\left|ab\right>
    .$$ $\left|ab\right>$ 也为$\hat{J}\_x^2+\hat{J}\_y^2$的本征矢,
本征值非负, 因此 $$a\geqslant b^2
    .$$ 定义上升算符$\hat{J}\_+$和下降算符$\hat{J}\_-$,
$$\hat{J}\_+=\hat{J}\_x+\mathrm{i}\hat{J}\_y,\ \ \hat{J}\_-=\hat{J}\_x-\mathrm{i}\hat{J}\_y
    .$$ 由于$\hat{J}^2$ 与任意$\hat{J}\_i$ 对易, 因此
$$\left[\hat{J}^2,\hat{J}\_\pm\right]=0
    .$$ 考虑上升与下降的对易关系 $$\begin{aligned}
        \left[\hat{J}\_+,\hat{J}\_-\right]&= \hat{J}\_x^2+\hat{J}\_y^2-\mathrm{i}\left(\hat{J}\_x\hat{J}\_y-\hat{J}\_y\hat{J}\_x\right)-\hat{J}\_-\hat{J}\_+ \\\\
        &= -2\mathrm{i}\left[\hat{J}\_x,\hat{J}\_y\right] 
    .\end{aligned}$$ 因此
$$\left[\hat{J}\_+,\hat{J}\_-\right]=2\hbar\hat{J}\_z
    .$$ 考虑$\hat{J}\_\pm$ 与$\hat{J}\_z$ 的对易关系有 $$\begin{aligned}
        \left[\hat{J}\_z,\hat{J}\_\pm\right]&= \hat{J}\_z\hat{J}\_x\pm\mathrm{i}\hat{J}\_z\hat{J}\_y-\hat{J}\_x\hat{J}\_z\mp\mathrm{i}\hat{J}\_y\hat{J}\_z \\\\
         &= \left[\hat{J}\_z,\hat{J}\_x\right]\mp\mathrm{i}\left[\hat{J}\_y,\hat{J}\_z\right]\\\\
         &=\mathrm{i}\hbar\hat{J}\_y\pm\hbar\hat{J}\_x
    .\end{aligned}$$ 于是有
$$\left[\hat{J}\_z,\hat{J}\_\pm\right]=\pm\hbar\hat{J}\_\pm
    .$$ 利用升降算符与$\hat{J}^2$ 的对易关系得
$$\hat{J}^2\hat{J}\_\pm\left|ab\right>=\hat{J}\_\pm\hat{J}^2\left|ab\right>=a\hat{J}\_\pm\left|ab\right>
    .$$ 因此, 经过$\hat{J}\_\pm$ 作用后的$\left|ab\right>$
仍为$\hat{J}^2$ 本征值为$a$的本征态. 类似地,
考察$\hat{J}\_z\hat{J}\_\pm\left|ab\right>$ 有 $$\begin{aligned}
        \hat{J}\_z\hat{J}\_\pm\left|ab\right>=\left(\pm\hbar\hat{J}\_\pm+\hat{J}\_\pm\hat{J}\_z\right)\left|ab\right>=\left(b\pm\hbar \right)\hat{J}\_\pm\left|ab\right>
    .\end{aligned}$$ 因此, 经$\hat{J}\_\pm$
作用后的$\hat{J}\_\pm\left|ab\right>$ 仍为$\hat{J}\_z$ 的本征态,
本征值较原本的$b$ 上升或下降$\hbar$. 于是有表示
$$\hat{J}\_\pm\left|ab\right>=c\_\pm\left|a,b\pm\hbar \right>
    .$$ 其中$c\_\pm$ 为待定常数. 又由于$b$
在之前的讨论中存在上下界(记为$b\_{\text{max}}$和$b\_{\text{min}}$), 因此有
$$\hat{J}\_+\left|ab\_{\text{max}}\right>=0,\ \ \hat{J}\_-\left|ab\_{\text{min}}\right>=0
    .$$ 进而
$$\hat{J}\_-\hat{J}\_+\left|ab\_{\text{max}}\right>=0,\ \ \hat{J}\_+\hat{J}\_-\left|ab\_{\text{min}}\right>=0
    .$$ 注意到 $$\begin{aligned}
        \hat{J}\_+\hat{J}\_-&= \hat{J}\_x^2+\hat{J}\_y^2-\mathrm{i}\left(\hat{J}\_x\hat{J}\_y-\hat{J}\_y\hat{J}\_x\right) \\\\
        &= \hat{J}\_x^2+\hat{J}\_y^2+\hat{J}\_z^2-\hat{J}\_z^2+\hbar\hat{J}\_z \\\\
        &=\hat{J}^2-\hat{J}\_z\left(\hat{J}\_z-\hbar \right)
    .\end{aligned}$$
类似地有$$\hat{J}\_-\hat{J}\_+=\hat{J}^2-\hat{J}\_z\left(\hat{J}\_z+\hbar\right)
    .$$ 作用于$\left|ab\right>$ 得到
$$a-b\_{\text{max}}\left(b\_{\text{max}}+\hbar \right)=0,\ \ a-b\_{\text{min}}\left(b\_{\text{min}}-\hbar \right)=0
    .$$ 联立并消去$a$ 得
$$b\_{\text{max}}\left(b\_{\text{max}}+\hbar \right)=b\_{\text{min}}\left(b\_{\text{min}}-\hbar\right)
    .$$
展开得$$b\_{\text{max}}^2-b\_{\text{min}}^2+\left(b\_{\text{max}}+b\_{\text{min}}\right)\hbar=0
    .$$ 因式分解有
$$\left(b\_{\text{max}}+b\_{\text{min}}\right)\left(b\_{\text{max}}-b\_{\text{min}}+\hbar \right)=0
    .$$ 方程的解为$b\_{\text{max}}=-b\_{\text{min}}$
或$b\_{\text{max}}-b\_{\text{min}}-\hbar=0$.
由于$b\_{\text{max}}>b\_{\text{min}}$, 后一项不能成立, 因此可以得到
$$b\_{\text{max}}=-b\_{\text{min}}
    .$$ 由于经过$\hat{J}\_\pm$ 作用可以使$b\_{\text{max}}$
和$b\_{\text{min}}$ 之间相互转化,
因此$b\_{\text{max}}-b\_{\text{min}}$必定为$\hbar$ 的整数倍, 即
$$b\_{\text{max}}-b\_{\text{min}}=2j\hbar 
    .$$ 其中$j$ 为整数或半整数.
于是有$$b\_{\text{max}}=j\hbar,\ \ b\_{\text{min}}=-j\hbar 
    .$$ 代入前述关系得 $$a=j\left(j+1\right)\hbar^2
    .$$ 为了方便, $\left|ab\right>$ 改写为$\left|jm\right>$, 其中$m$
的可能取值为$-j,-j+1,\ldots,j-1,j$. 于是可以确定$\hat{J}\_\pm$
作用后的系数: $$\begin{aligned}
        \left|c\_\pm\right|^2&=\left<jm\right|\hat{J}\_\mp\hat{J}\_\pm\left|jm\right>\\\\
        &= \left<jm\right|\left[\hat{J}^2-\hat{J}\_z\left(\hat{J}\_z\pm\hbar \right)\right]\left|jm\right> \\\\
        &= \left[j\left(j+1\right)\hbar^2-m\hbar\left(m\hbar\pm\hbar \right)\right]\left<jm|jm\right> \\\\
        &=\left[j\left(j+1\right)-m\left(m\pm 1\right)\right]\hbar^2
    .\end{aligned}$$ 规定$c\_\pm$ 为实数, 则有
$$c\_\pm=\sqrt{j\left(j+1\right)-m\left(m\pm 1\right)} \hbar
    .$$ 经上述推导总结得 $$\begin{cases}
            \hat{J}^2\left|jm\right>=j\left(j+1\right)\hbar^2\left|jm\right>\\\\
            \hat{J}\_z\left|jm\right>=m\hbar^2\left|jm\right>\\\\
            \hat{J}\_\pm\left|jm\right>=\sqrt{j\left(j+1\right)-m\left(m\pm 1\right)} \hbar\left|j,m\pm 1\right>
        \end{cases}
    .$$

## 轨道角动量

由角动量的定义
$$\hat{\boldsymbol{L}}=\hat{\boldsymbol{x}}\times \hat{\boldsymbol{p}}
    .$$ 推导角动量在位置表象的表示.
其中$$\hat{\boldsymbol{x}}=\begin{pmatrix} x \\\\ y\\\\ z \end{pmatrix},\ \ \hat{\boldsymbol{p}}=-\mathrm{i}\hbar\begin{pmatrix}\frac{\partial{}}{\partial{x}}  \\\\ \frac{\partial{}}{\partial{y}}\\\\ \frac{\partial{}}{\partial{z}} \end{pmatrix}
    .$$ 计算上述外积有$$\begin{cases}
        \hat{L}\_x=-\mathrm{i}\hbar(y\frac{\partial{}}{\partial{z}}-z\frac{\partial{}}{\partial{y}})\\\\
        \hat{L}\_y=-\mathrm{i}\hbar(z\frac{\partial{}}{\partial{x}}-x\frac{\partial{}}{\partial{z}})\\\\
        \hat{L}\_z=-\mathrm{i}\hbar(x\frac{\partial{}}{\partial{y}}-y\frac{\partial{}}{\partial{x}})
    \end{cases}
    .$$

## 自旋1/2体系

对于自旋体系, 自旋角动量算符常用$\hat{\boldsymbol{S}}$ 表示,
并使用$\left|sm\_s\right>$ 表示本征态.
自旋1/2体系(如电子自旋)是一个二维矢量空间, $\hat{S}^2$ 和$\hat{S}\_z$
的两个共同本征矢为$\left|\frac{1}{2},\frac{1}{2}\right>$
(即$\left|s\_z+\right>$)和$\left|\frac{1}{2},-\frac{1}{2}\right>$
(即$\left|s\_z-\right>$).
习惯上记该本征空间中$\left|\alpha\right>=\left|\frac{1}{2}.\frac{1}{2}\right>$,
$\left|\beta \right>=\left|\frac{1}{2},-\frac{1}{2}\right>$,
分别称为自旋向上和自旋向下, 则对任意的态矢可以展开为
$$\left|\gamma\right>=a\left|\alpha\right>+b\left|\beta \right>,\ \ \left|a\right|^2+\left|b\right|^2=1
    .$$ 用$\left|\alpha\right>$ 和$\left|\beta \right>$
作为基组展开自旋1/2空间, 则有
$$\boldsymbol{\alpha}=\begin{pmatrix} 1 \\\\ 0 \end{pmatrix},\ \ \boldsymbol{\beta }=\begin{pmatrix} 0 \\\\ 1 \end{pmatrix}
    .$$ $\hat{S}^2$在该基组上的表示为
$$S^2=\frac{3}{4}\hbar^2\begin{pmatrix}
            1&0\\\\0&1
        \end{pmatrix}
    .$$ 类似地, 由前述算符的作用定义, $\hat{S}\_z$, $\hat{S}\_+$
和$\hat{S}\_-$ 的表示为 $$S\_z=\frac{1}{2}\hbar\begin{pmatrix}
            1&0\\\\0&-1
        \end{pmatrix}
        ,\ \ S\_+=\hbar\begin{pmatrix}
            0&1\\\\0&0
        \end{pmatrix},\ \ 
        S\_-=\hbar\begin{pmatrix}
            0&0\\\\1&0
        \end{pmatrix}
    .$$ 有由上升、下降算符的$\hat{S}\_x$,$\hat{S}\_y$ 表示有
$$S\_x=\frac{1}{2}\hbar\begin{pmatrix}
            0&1\\\\1&0
        \end{pmatrix}
        ,\ \ S\_y=\frac{1}{2}\hbar\begin{pmatrix}
            0&-\mathrm{i}\\\\ \mathrm{i}&0
        \end{pmatrix}
    .$$ $2\times 2$ 的矩阵是4维的, 基的个数为4. 因此,
对于任意的$2\times 2$ 矩阵, 都可以将其表示为4个线性无关的$2\times 2$
矩阵. 其中的一个取法为 $$I=\begin{pmatrix}
            1&0\\\\0&1
        \end{pmatrix}
        ,\ \ \sigma\_x=\begin{pmatrix}
            0&1\\\\1&0
        \end{pmatrix}
        ,\ \ \sigma\_y=\begin{pmatrix}
            0&-\mathrm{i}\\\\\mathrm{i}&0
        \end{pmatrix}
        ,\ \ \sigma\_z=\begin{pmatrix}
            1&0\\\\0&-1
        \end{pmatrix}
    .$$ 其中$\sigma\_x$, $\sigma\_y$, $\sigma\_z$ 被称为Pauli矩阵. 令
$\boldsymbol{\sigma}$ 是Pauli矩阵的线性组合, 可以表示为三维矢量,
被称作Pauli矢量. Pauli矩阵满足如下的重要运算性质:
$$\left[\sigma\_i,\sigma\_j\right]=2\mathrm{i}\varepsilon\_{ijk}\sigma\_k,\ \ \left\\{\sigma\_i,\sigma\_j\right\\}=2\delta\_{ij}I
    .$$
由Pauli矩阵积$\sigma\_i\sigma\_j=\delta\_{ij}I+\mathrm{i}\varepsilon\_{ijk}\sigma\_k$,
对于任意的可与Pauli矩阵交换的张量$a$,$b$, 满足
$$ab\sigma\_i\sigma\_j=ab\left(\delta\_{ij}I+\mathrm{i}\varepsilon\_{ijk}\sigma\_k\right)
    .$$ 因而
$$a\sigma\_ib\sigma\_j=ab\left(\delta\_{ij}I+\mathrm{i}\varepsilon\_{ijk}\sigma\_k\right)
    .$$
考虑$$\left(\boldsymbol{a}\cdot \boldsymbol{\sigma}\right)\left(\boldsymbol{b}\cdot \boldsymbol{\sigma}\right)=\left(a\_1\sigma\_x+a\_2\sigma\_y+a\_3\sigma\_z\right)\left(b\_1\sigma\_x+b\_2\sigma\_y+b\_3\sigma\_z\right)
    .$$
展开得$$\left(a\_1b\_1+a\_2b\_2+a\_3b\_3\right)I+\mathrm{i}\left[\left(a\_1b\_2-a\_2b\_1\right)\sigma\_z+\left(a\_2b\_3-a\_3b\_2\right)\sigma\_x+\left(a\_3b\_1-a\_1b\_3\right)\sigma\_y\right]
.$$ 因此有
$$\left(\boldsymbol{a}\cdot \boldsymbol{\sigma}\right)\left(\boldsymbol{b}\cdot \boldsymbol{\sigma}\right)=\left(\boldsymbol{a}\cdot \boldsymbol{b}\right)I+\mathrm{i}\left(\boldsymbol{a}\times \boldsymbol{b}\right)\cdot \boldsymbol{\sigma}
.$$

## 角动量的耦合

考虑两个相互正交的角动量空间的角动量算符之和
$$\boldsymbol{\hat{J}}=\boldsymbol{\hat{J}}\_1+\boldsymbol{\hat{J}}\_2
    .$$ 两算符的和依然符合角动量算符的定义, 仍然是一个角动量算符.
在一个$\boldsymbol{\hat{J}}\_1$, $\boldsymbol{\hat{J}}\_2$
均有意义的体系中, 可以验证$\hat{J}\_1^2$, $\hat{J}\_{1z}$, $\hat{J}\_2^2$
和$\hat{J}\_{2z}$ 是彼此对易的. 例如对于$\hat{J}\_1^2$和$\hat{J}\_2^2$
的共同本征态$\left|j\_1j\_2\right>$,
有$$\hat{J}\_1^2\hat{J}\_2^2\left|j\_1j\_2\right>=j\_1j\_2\left(j\_1+1\right)\left(j\_2+1\right)\hbar^{4}\left|j\_1j\_2\right>=\hat{J}\_2^2\hat{J}\_1^2\left|j\_1j\_2\right>
    .$$ $\hat{J}\_1^2$, $\hat{J}\_{1z}$, $\hat{J}\_2^2$ 和$\hat{J}\_{2z}$
的共同本征态$\left\\{\left|j\_1j\_2m\_1m\_2\right>\equiv \left|j\_1m\_1\right>\otimes\left|j\_2m\_2\right>\right\\}$在$j\_1$,
$j\_2$ 确定的情况下, 维度为$m\_1$, $m\_2$ 独立取值可能的组合,
即$\left(2j\_1+1\right)\left(2j\_2+1\right)$. 考虑$\hat{J}^2$,
$\hat{J}\_z$, $\hat{J}\_1^2$, $\hat{J}\_2^2$. 由于它们是彼此对易的,
因此共同的本征态$\left\\{\left|jmj\_1j\_2\right>\right\\\}$也可以作为总角动量空间的基.
下面验证耦合后基组的维数与未耦合相等. 考虑基组之间的幺正变换
$$\begin{cases}
            \left|jmj\_1j\_2\right>=\sum\_{m\_1,m\_2}\left|j\_1j\_2m\_1m\_2\right>\left<j\_1j\_2m\_1m\_2|jmj\_1j\_2\right>\\\\
            \left|j\_1j\_2m\_1m\_2\right>=\sum\_{j,m}\left|jmj\_1j\_2\right>\left<jmj\_1j\_2|j\_1j\_2m\_1m\_2\right>
        \end{cases}
    .$$ 对应矩阵$C$ 的矩阵元$\left<j\_1j\_2m\_1m\_2|jmj\_1j\_2\right>$
称为Clebsch-Gordan矢量耦合系数, 简称CG系数. 由于$C$变换后保持内积不变,
可以得到 $$\begin{cases}
            \sum\_{m\_1,m\_2}\left<jmj\_1j\_2|j\_1j\_2m\_1m\_2\right>\left<j\_1j\_2m\_1m\_2|j'm'j\_1j\_2\right>=\delta\_{jj'}\delta\_{mm'}\\\\
            \sum\_{j,m}\left<j\_1j\_2m\_1m\_2|jmj\_1j\_2\right>\left<jmj\_1j\_2|j\_1j\_2m\_1'm\_2'\right>=\delta\_{m\_1m\_1'}\delta\_{m\_2m\_2'}
        \end{cases}
    .$$ 根据习惯, CG系数取实数, 因此矩阵$C$ 为正交矩阵.
矩阵元不为0须满足 $$\begin{cases}
            m=m\_1+m\_2\\\\
            \left|j\_1-j\_2\right|\leqslant j\leqslant j\_1+j\_2
        \end{cases}
    .$$ 前一个条件的证明,
考虑$$\left(\hat{J}\_z-\hat{J}\_{1z}-\hat{J}\_{2z}\right)\left|jmj\_1j\_2\right>=0
    .$$ 因此有 $$\left(m-m\_1-m\_2\right)\left|jmj\_1j\_2\right>
    .$$
