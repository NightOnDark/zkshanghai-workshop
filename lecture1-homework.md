# 第1课 课后作业

## 第1题 Exercise 1: Currently, you can only select adjacent pairs of nodes to check. Would the proof still be zero knowledge if you could pick arbitrary pairs of nodes to check?

如果可以选择任意两点，通过多次请求就可以知道两个不同点之间的关系，通过知道每两个点的颜色是否相同就可以推断出所有点互相之间的颜色关系，所以这种情况下不是零知识的。

## 第2题 zkmessage.xyz
1.解释为什么你需要生成并保存一个“秘密值” 。

“秘密值”类似于公钥体系中的私钥，拥有秘密值也就拥有了身份的所属权。

2.用白话写出 ZK 中正在证明的陈述。

先验证秘密值是账户的管理者，再验证是否group中的一员，最后验证group中的各个公钥都在group中。

3.从不同的浏览器或计算机登录到相同的 zkmessage 帐户。 解释为什么 zkmessage 不能像大多数社交应用程序一样，只使用简单的“用户名/密码” 。

直接像大多数应用程序一样会需要有机构管理用户名/密码，这些都属于隐私信息。使用zk技术能保护自己的用户身份信息。
