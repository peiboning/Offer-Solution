# 剑指OFFER面试题编程练习

## 2.3数据结构
- 数组
- 字符串
- 链表
- 树
- 栈
### 2.3.1数组
数组，占据一块连续的内存并按照顺序存储数据。优于数组中的内存是连续的，于是可以根据下表在O(1)时间读写任何元素，因此它的时间效率很高。**可以利用数组与链表来组成哈希表（JDK1.8以前，HashMap采用数组+链表，JDK1.8采用了红黑树，当链表长度太长，链表转化为红黑树，利用红黑树快速增删查改的特点提高HashMap的性能）**。

##### 面试题3：数组中重复的数字
解题思路：
- 在可以改变原始数组的情况下，可以利用改变数组，使其按顺序排序，当发现num[i]==num[num[i]]时，则说明有重复数字。时间复杂度O(n),空间复杂度O(1)。(DuplicationInArray)
- 在不可以改变原始数组时，可以利用辅助数组。空间复杂度O(n),时间复杂度O(n)。
- 在不可以改变原始数组时，也可以利用二分查找的思想，将数值范围不断切分，并查找数值范围内数字出现的个数，当出现的个数大于数值范围时，则说明在该范围内存在重复数字。**但，这种方法无法保证找出所有重复的数字。例如在1~2范围内，2重复出现两次，1不出现，则计数等于2，并且不大于该范围，此时该算法不能确定每个数字出现的次数，所以不能保证找到所有重复的数字**。(DuplicationInArrayNoEdit)

##### 面试题4：二维数组中的查找
**题目**：在一个二维数组众，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序，请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


解题思路：**通过具体的例子找到其中的规律**。从一个具体的二维数组的右上角开始分析，就能找到查找的规律，从而解决问题的突破口。

### 2.3.2字符串


### 2.3.3链表
链表是一种动态数据结构，是因为在创建链表时，无须知道链表的长度。当插入一个节点时，我们只需要为新的节点分配内存，然后调整指针的指向来确保新节点被连接到链表中。内存分配不是在创建链表时一次性完成的，而是每添加一个节点分配一次内存。由于没有闲置的内存，链表的空间效率比数组高。




##### 面试题6：从尾到头打印链表
**题目**：输入一个链表的头节点，从尾到头反过来打印出每个节点的值。

解题思路：利用栈，先进先出。先遍历整个链表，将链表值保存在栈中，再依次出栈打印即可。

### 2.3.4 树

在面试时，经常会问到二叉树。

树的遍历方式：
- 前序遍历：先访问根节点，再访问左子节点，最后访问右子节点。
- 中序遍历：先访问左子节点，再访问根节点，最后访问右子节点。
- 后序遍历：先访问左子节点，再访问右子节点，最后访问跟节点。

二叉树的两个特例：堆和红黑树。

- 堆分为最大堆和最小堆。在最大堆中根节点最大，在最小堆中根节点最小。有很多需要快速找到最大值和最小值的问题都可以用堆来解决。
- 红黑树是把树中的节点定义为红、黑两种颜色，并通过规则确保从根节点到叶子节点的最长路径的长度不超过最路径的两倍。

##### 面试题7：重建二叉树
**题目**：输入某二叉树的前序遍历和中序遍历的结果。请重建该二叉树。

解题思路：在二叉树的前序遍历中，第一数字总是树的根节点的值。但在中序遍历中，根节点的中再序列的中间。左子树位于其左边，右子树位于其右边。通过遍历前序，可以在中序中判断出哪一部分为左子树和右子树。从而通过递归，重建出二叉树。


#### 面试题8：二叉树的下一个节点
**题目**：给定一棵二叉树和其中的节点，如何找出中序遍历的下一个节点？树中的节点除了两个分别指向左和右子节点的指针，还有一个指向父节点的指针。

解题思路：注重前序遍历、中序遍历和后序遍历！！！从中找规律，即可解题。


### 2.3.5 栈和队列

- 栈：先进后出
- 队列：先进先出

#### 面试题9：用两个栈实现队列
**题目**：用两个栈实现一个队列。即实现，在队尾添加元素和删除队列第一个元素。

解题思路：给定两个stack，分别是stack1和stack2. 用stack1来存储输入元素，当要删除第一个元素时，先判断stack2是否为空，为空则将stack1的元素按顺序pop出来并压如stack2（c->b->a变成了a->b->c），然后将stack2的最后一个元素删除；若不为空，则直接将stack2的最后一个元素删除即可。

## 2.4算法和数据操作

重点：
- 排序和查找：二分查找、归并排序和快速排序。
- 二维数组，可以尝试回溯法（用递归实现）。
- 求某个问题的最优解，可以尝试使用动态规划。（进一步提问，可能需要用贪婪算法求最优解）
- 位运算

### 2.4.1 递归与循环

- 递归是一个函数的内部调用这个函数自身。
- 循环则是通过设置计算的初始值及终止条件，在一个范围内重复计算。

递归缺点：调用函数是有时间和空间的消耗（每一次函数调用，要在内存栈中分配空间以保存参数、返回变量及临时变量）

#### 面试题10：斐波那契数列
**题目一**：求斐波那切数列的第n项。

解题思路：这道题用递归效率低。因为在计算数列时，有很多重复的数据。
采用循环，每一次循环保存中间项，方便下一次计算。f(n)=f(n-1)+f(n-2)

**题目二**：青蛙跳台阶问题，一只青蛙可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个n级台阶总共有多少种跳法。
解题思路：类似。当n>2时，第一跳有两种选择：第一种是跳1级台阶，此时跳法数目等于后面剩下的n-1级台阶的跳法数目；第二种是跳2级台阶，此时跳法数目等于后面剩下的n-2级台阶的跳法数目。f(n)=f(n-1)+f(n-2)

### 2.4.2 查找和排序
查找：顺序查找、二分查找（数组必须是按顺序的）、哈希表查找（它能够在O(1)时间内查找某一元素，但是需要额外的空间来实现哈希表）和二叉排序查找。

排序：插入排序、冒泡排序、归并排序、*快速排序**。

#### 面试题11：旋转数组的最小数字
**题目**：把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组{3,4,5,1,2}位{1,2,3,4,5}的一个旋转，该数组最小值为1.

解题思路：可以注意到旋转数组是由两个顺序的子数组组成的，左子数组和右子数组。最小的数字应该是右子数组的第一个数。我们可以利用二分查找的思路来做。

指针left指向第一个元素，指针right指向最后一元素，在每一次循环的过程中，选择中间元素num[middle]进行比较。

a.)如果num[middle]>=num[left],说明middle在左子数组中，所以应该令left等于middle；

b.)如果num[middle]<=num[right],则说明middle在右子数组中，所以应该令right等于middle。

当right-left等于1时，则最小数就是num[right]。因为，此时left是左子数组最后一个数字，right是右子数组第一个数字，右子数组第一个数即最小数。

如果num[left]==num[right] 并且 num[left]==num[middle]，则说明在left到right区间内，无法通过上述规则找出最小数，例如{1,1,1,1,1,0,1}。应该通过线性搜索，找到最小数字。

### 2.4.3 回朔法

回朔法适合有多个步骤组成的问题，并且每一个步骤都有多个选项需要尝试。如果下一次尝试不满足约束条件，那么只好回溯到上一个问题，如果上一个节点所有可能的选项都已经试过了，并不能达到满足约束条件的终结状态，则再次回溯到上一个节点。
回溯法经常采用递归的方式实现。


#### 面试题 12： 矩阵中的路径
**题目**：设计一个函数，用来判断在一个矩阵中是否存在一条包含某字符串的所有字符的路径。路劲可以从矩阵的任意一格开始，每一步可以在矩阵中向上，左，右和下移动。如果一条路径经过了矩阵的某一格子，则不能再次进入。


解题思路：在每一步中，都访问节点附近的邻近4个节点，查找下一个字符是否等于字符串中的字符。
若匹配上，则继续查找，若四个节点都没有匹配上，则回退到上一层。

'''python
def hashPath(matrix, str):
    chars = str.tochar()
    visited = boolean[matrix.shape[0]][matrix.shape[1]]
    for(i in range(matrix.shape[0])):
        for(j in range(matrix.shape[1]))):
	    if(hashPathCore(matrix, i, j, chars, 0, visited))
	        return true
    return false
   
def hashPathCore(matrix, i, j, chars, index, visited):
    if index == chars.length:
        return true
    if i>=0 and i< matrix.shape[1] and j>=0 and j < matrix.shape[1] and chars[index] == matrix[i][j] and ~visited[i][j]:
        visited[i][j] = true
        result = hashPathCore(matrix, i+1, j , chars, index+1, visited) ||
		hashPathCore(matrix, i-1, j , chars, index+1, visited) ||
		hashPathCore(matrix, i, j+1 , chars, index+1, visited) ||
		hashPathCore(matrix, i, j-1 , chars, index+1, visited)
	if result == false:
	    visited[i][j] = false
	return ture
    return false'''
