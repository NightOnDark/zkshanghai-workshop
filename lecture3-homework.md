# 第3课 课后作业

## 二次非剩余
完备性：
如果$QR(m,x)=0$ ，在协议中，双方都按照协议执行时，当$b=1$时，$y=s^2$，Prover返回$QR(m,y)=QR(m,s^2)=1$给Verifier，与b值相同；当$b=0$时，$y=s^2x$，Prover返回$QR(m,y)==QR(m,s^2x)=QR(m,x)=0$给Verifier，与b值相同。
可靠性：
如果$QR(m,x)=1$ ，在协议中，无论$y=s^2$或者$y=s^2x$，Prover如果正确执行就只会返回1，所以只有1/2的正确性，如果。Prover如果不正确执行就只会返回0，依旧是1/2的正确性。

## 二次剩余
完备性：
$QR(m,x)=1$ ，在协议中，双方都按照协议执行时，当$b=1$时，$u=st$，则$u^2=s^2t^2=xt^2=y$,验证者接受验证；当$b=0$时，$u=t$，则$u^2x=xt^2=y$,验证者接受验证。
可靠性：
如果$QR(m,x)=0$ ，在协议中，$u=t$时，则$u^2x=xt^2=y$，通过验证；$u=st$时，则等式不成立，不通过验证。所以说服验证者的概率是1/2。
知识可靠性：
在同一$s$的情况下，验证者如果能同时询问$b=1$与$b=0$的情况，将获得$t,st$,因此将得到秘密$s=st/t$。
零知识：
当去掉Prover的操作，Verifier随机选取$u$值，根据$b$值计算出$y$值。
Verifier回到协议第一步，模拟Prover提供的$y$
接着根据b值继续接下来的步骤。
整个过程与实际交互不可区分

## 双线性自映射意味着DDH的失效
计算$e(\alpha g,\beta g)=e(y,g)$是否成立即可。
