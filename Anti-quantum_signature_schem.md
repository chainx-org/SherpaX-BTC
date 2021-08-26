## 事情概述
量子计算的好处是： 可以快速计算，超出我们当前CPU的计算速度。 
当前计算机没法暴力破解的密码， 但在以快速计算著称的量子计算机去计算，就能穷举。
比如，我们区块链的基础账户密码学体系， 椭圆曲线。 
知道pubkey，知道椭圆曲线，就能穷举privkey。

## 解决量子计算办法的核心思想
   因为量子计算的核心攻击，就是暴力穷举破解。
   那如何抵抗量子计算呢？
   两种思路： 
   1， 数据量无穷， 比如对不确定数量的文字 做hash算法。
   2， 不给出答案， 在没有答案的情况下，没法去穷举暴力破解。
   
## 具体解决方法
   聚合签名和 新型MAST合约结合。
  以 A，B，C 三个用户组成的门限签名为例：
  ```
        root
      /      \
   branch1    (Hidden computing paradigm script)
   /      \
 branch2   BC
 /    \
 AB    AC
 ```
 AB, AC, BC 代表聚合签名。
 
 Hidden computing pradigm script： 代表branch1 在参照右分支上的(Hidden computing paradigm script) 算法算出root根。
 
 在账户被操作前， 我们只需要把root存在链上， 且每次这个结构生成的账户只能使用一次。 因为当使用过一次后， 叶子节点上的聚合公钥就暴露了。

