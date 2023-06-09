# 第5课 课后作业

## 第1题 
1. Commit阶段：Prover随机选择一个多项式$f(X)$，$C=[f(\tau)]_1$
2. Open阶段：$\pi=((f(\tau)-y)/(\tau -z))\dot [1]_1$
3. Verify阶段：$e(C-[y]_1,[1]_2)= e(\pi,[\tau]_2-[z]_2)$ 则$e([f(\tau)]_1-[y]_1,[1]_2)= e(((f(\tau)-y)/(\tau -z))_1,[\tau]_2-[z]_2)$成立
完成伪造承诺

## 第2题
1. 存在向量$(m_0,m_1,...,m_q),求多项式$多项式$P(X){\textstyle \sum_{i=0}^{q}(m_i \prod_{j=0,j\neq i}^{q}\frac{X-j}{i-j})}$,Prover计算承诺$C=[P(\tau)]_1$
2. 因为$p(i)=m_i$,所以Open阶段根据单点验证或者多点验证分别使用第1题或者第2题的证明验证方法

## 第3题
1. 多项式$P(X)$,Prover计算承诺$C=[P(\tau)]_1$
2. 根据拉格朗日插值多项式，存在多项式$I(X)={\textstyle \sum_{i=0}^{k-1}(y_i  \prod_{j=0,j\neq i}^{k-1}\frac{X-z_j}{z_i-z_j})} $,在$z_0,z_1,...,z_{k-1}$点都为零
3. 因为$z_0,z_1,...,z_k-1$点都为零点，存在$Z(X)=(X-z_0)...(X-z_{k-1})$,商余为$q(X)=\frac{P(X)-I(X)}{Z(X)}$,打开承诺的证明 $\pi=[q(\tau)]_1$
4. $e(\pi,[Z(\tau)]_2)=e(C-[I(\tau)]_1,[1]_2)$
