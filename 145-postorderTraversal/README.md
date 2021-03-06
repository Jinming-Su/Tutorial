##题目分析

给定一棵二叉树，求出它的后序遍历序列，要求使用非递归

##题解思路

如果使用递归，那就是遍历树的经典题了。只需要知道后序遍历是根节点放在最后。直接对于每一个节点，先递归它的左孩子，再递归它的右孩子，最后再将自己放在序列末。时间空都是复杂度`O(n)`。

换成非递归也非常的简单，只需要自己手动模拟递归栈即可。按照递归的思路，我们要先遍历完某个节点的左孩子，再遍历右孩子，最后回溯，所以我们在进入某个节点时先将它置入栈顶，此时应该设置一个标记（比如标记等于1），表示下次弹出这个节点的时候表示需要向下搜索。那么当弹出某个标记为1的点时我们怎么安排入栈顺序呢？回忆一下后序遍历的次序是左右中，而栈又是先进后出故而入栈顺序应该是中右左，所以把这个标记为1的点入栈，记得入栈后将标记修改（比如修改成2），表示下次这个点出栈是要向上回溯；紧接着将它的右孩子和左孩子相继入栈（记得置标记）。当弹出一个标记为2的点时，便可以直接将值存入答案序列。

下面对于原题的样例举个例子：
我们先假设原树节点的编号等于值，按照算法的思路
+ 初始放入根节点，栈为：{1, 1}|(前面为栈顶，后面为栈尾，{}对中第一个键值表示节点编号，第二个表示入栈标记)
+ 弹出栈顶{1,1}，按照中右左的顺序入栈，栈为：{2,1},{1,2}|
+ 弹出栈顶{2,1}，按照中右左的顺序入栈，栈为：{3,1},{2,2},{1,2}|
+ 弹出栈顶{3,1}，按照中右左的顺序入栈，栈为：{3,2},{2,2},{1,2}|
+ 弹出栈顶{3,2}，此时标记为2，将节点3对应的val放入序列，此时序列为：{3}，栈为{3,2},{1,2}|
+ 弹出栈顶{2,2}，此时标记为2，将节点2对应的val放入序列，此时序列为：{3,2}，栈为{1,2}|
+ 弹出栈顶{1,2}，此时标记为2，将节点1对应的val放入序列，此时序列为：{3,2,1}，栈为空|
+ 算法结束。
