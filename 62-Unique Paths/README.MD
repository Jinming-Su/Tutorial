## 题目分析：
现有一个大小为`M*N`的网格，问从左上角到右下角的方案数目。  
`M`与`N`不大于100。
### 解题思路(1):   
经典的递推入门题目。乍一看题面中M与N的大小规模，默默估算下最大答案为C(200,100,远远大于Int的范围。而重新审视我们所要写的函数所返回的类型为int，这说明不必担心答案超出int的范围。  
使用递推式`path[i][j] = path[i-1][j] + path[i][j-1]`即可，注意下边界的初始化。时间复杂度为`O(N*M)`。
### 解题思路(2):   
由于从左上角到右下角的总步数为`N+M`，仅需从其中选出M步进行向下的运动，剩下的N步向右运动即可，因此总方案数可用组合数计算公式`C(M+N,N)`，便可计算出。时间复杂度为`O(N+M)`。因此方法有些大材小用，并不给出相应代码，读者可以自行实现。
