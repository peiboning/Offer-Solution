# 剑指OFFER面试题编程练习

## 2.3数据结构
- 数组
- 字符串
- 链表
- 树
- 栈
### 2.3.1数组
数组，占据一块连续的内存并按照顺序存储数据。优于数组中的内存是连续的，于是可以根据下表在O(1)时间读写任何元素，因此它的时间效率很高。**可以利用数组与链表来组成哈希表（JDK1.8以前，HashMap采用数组+链表，JDK1.8采用了红黑树，当链表长度太长，链表转化为红黑树，利用红黑树快速增删查改的特点提高HashMap的性能）**。

#### 面试题3：数组中重复的数字
解题思路：
- 在可以改变原始数组的情况下，可以利用改变数组，使其按顺序排序，当发现num[i]==num[num[i]]时，则说明有重复数字。时间复杂度O(n),空间复杂度O(1)。(DuplicationInArray)
- 在不可以改变原始数组时，可以利用辅助数组。空间复杂度O(n),时间复杂度O(n)。
- 在不可以改变原始数组时，也可以利用二分查找的思想，将数值范围不断切分，并查找数值范围内数字出现的个数，当出现的个数大于数值范围时，则说明在该范围内存在重复数字。**但，这种方法无法保证找出所有重复的数字。例如在1~2范围内，2重复出现两次，1不出现，则计数等于2，并且不大于该范围，此时该算法不能确定每个数字出现的次数，所以不能保证找到所有重复的数字**。(DuplicationInArrayNoEdit)

#### 面试题4：二维数组中的查找
**题目**：在一个二维数组众，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序，请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


解题思路：**通过具体的例子找到其中的规律**。从一个具体的二维数组的右上角开始分析，就能找到查找的规律，从而解决问题的突破口。