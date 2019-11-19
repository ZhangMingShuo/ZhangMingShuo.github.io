# 概率 
## 事件与概率

```latex
(1)
1.随机试验:1.相同条件可重复;2.试验结果多样性，一切结果可以知道;3.试验前不确定具体结果 \\ 
2.样本空间\Omega:E是随机试验,E的一切可能基本结果组成的全体称为样本空间,记作\Omega \\
3.事件 \\
4.不可能事件\phi \subset \Omega \\
5.\Omega \subset \Omega \\
(2).事件运算 \\
1.和 A+B \\
2.积 AB \\
3.差 A-B A发生且B不发生的事件 \\
4.补 \bar{A} \\
(3).事件关系 \\
1.A,B对立\to AB= \Phi, A+B= \Omega \to B=\bar{A} \\
2.A=(A-B)+AB \\
3.A+B=(A-B)+AB+(B-A) \\
(4).概率定义与基本性质 \\
(一)E是随机试验,\Omega是样本空间, \forall A \subset \Omega 定义P(A)为 \\
```
# 线性代数
## 判断矩阵的特征值与其伴随矩阵的特征值的关系
```latex
AA^*=A^*A=|A|E \\
A \alpha =\lambda \alpha \\
A^*A \alpha = A^* \lambda \alpha \\
A^*A \alpha = |A| \alpha \\
A^* \alpha = \frac{|A|}{\lambda} \alpha \\
```
# 微积分
## 判断空间中两向量是否共面
```latex
L_1上一点M_1,\vec{s_1}与L_1共线,L_2上一点M_2,\vec{s_2}与L_2共线。\\
若(\vec{s_1} \times \vec{s_2})\cdot \overrightarrow{M_1M_2} = 0, 则L_1与L_2共面，反之异面\\
         
```
## 过一直线L的平面束方程
```latex
过一直线L \begin{cases}
              a_1x+b_1y+c_1z=0& \text{ }\\
              a_2x+b_2y+c_2z=0& \text{ }
            \end{cases} 的平面束为: a_1x+b_1y+c_1z+\lambda(a_2x+b_2y+c_2z)=0
```
## 对弧长的曲面积分
```latex
已知L的参数方程:\begin{cases}
              x=\phi(t)& \text{ }\\
              y=\psi(t)& \text{ }
            \end{cases} 
对弧长L的曲面积分 \int_{L}f(x,y)ds=\int^{\beta}_{\alpha}f[\phi(t),\psi(t)]\sqrt{\phi^{'2}(t)+\psi^{'2}(t)}dt(\alpha<\beta)
```
## 对坐标的曲面积分
```latex
\int_{L}P(x,y)dx=\int^{\beta}_{\alpha}P[\phi(t),\psi(t)]\phi^{'}(t)dt \\
\int_{L}Q(x,y)dy=\int^{\beta}_{\alpha}Q[\phi(t),\psi(t)]\psi^{'}(t)dt 
```
## 格林公式
```latex
设闭区域D由分段光滑的曲线L围成，函数P(x,y)及Q(x,y)在D上具有一阶连续偏导数\\
\iint\limits_{D}(\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y})dxdy=\oint_LPdx+Qdy,L是D的取正向的边界闭曲线.
```
## 三重积分的物理意义
```latex
占有空间区域\Omega的物体，在点(x,y,z)有体密度f(x,y,z)则质量是\iiint\limits_{\Omega}f(x,y,z)dv
```
## 高斯公式
```latex
设空间闭区域\Omega是由分片光滑的闭曲线\Sigma所围成，P(x,y,z),Q(x,y,z),R(x,y,z)在\Omega上具有一阶连续偏导数,
\oiint\limits{\Sigma}Pdydz+Qdzdx+Rdxdy=\iiint\limits_{\Omega}(frac{\partial P}{\partial x}+frac{\partial Q}{\partial y}+frac{\partial R}{\partial z})dv \\
\oiint\limits{\Sigma}(Pcos\alpha+Qcos\beta+Rcos\gammma)dS=\iiint\limits_{\Omega}(frac{\partial P}{\partial x}+frac{\partial Q}{\partial y}+frac{\partial R}{\partial z})dv \\
```
