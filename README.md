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
```python
def preOrder(root):
    if root is None:
        return
    //operation on root
    preOrder(root.left)
    preOrder(root.right)
    
 ```

- 中序遍历：先访问左子节点，再访问根节点，最后访问右子节点。
```python
def inOrder(root):
    if root is None:
        return
    inOrder(root.left)
    //operation on root
    inOrder(root.right)
    
 ``` 

- 后序遍历：先访问左子节点，再访问右子节点，最后访问跟节点。
```python
def postOrder(root):
    if root is None:
        return
    postOrder(root.left)
    postOrder(root.right)
    //operation on root
    
 ``` 

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

**题目三**：覆盖矩阵，我们可以用2*1的小矩形横着或者竖着去覆盖更大的矩形。请问用n个2*1的小矩形无重叠地覆盖一个2*n的大矩形，总共有多少种方法？
当第一次覆盖2*1的小矩阵（竖着放），则后面的覆盖方法为f(n-1);
当第一次覆盖2*2的小矩阵（两个横着放），对应下方的2*(n-2)的小矩阵摆放必然是确定的，所以后面的覆盖方法为f(n-2)。
所以总的覆盖方法为：f(n) = f(n-1) + f(n-2); 依旧是斐波那契数列的算法。


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

```python
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
        result = hashPathCore(matrix, i+1, j , chars, index+1, visited) or
		hashPathCore(matrix, i-1, j , chars, index+1, visited) or
		hashPathCore(matrix, i, j+1 , chars, index+1, visited) or
		hashPathCore(matrix, i, j-1 , chars, index+1, visited)
	if result == false:
	    visited[i][j] = false
	return ture
    return false
 ```


#### 面试题 13： 机器人的运动范围
**题目**：地上有一个m行n列的方格。一个机器人从坐标(0,0)的格子开始移动，他每次可以向左，右，上和下移动一格，但不能进入坐标和列坐标的数位之和大于k的格子。例如，给定k=18时，机器人可以进入（35,37），因为3+5+3+7=18；
但是不能进入(35,38),因为3+5+3+8=19。

解题思路：从坐标(0,0)开始回溯计算可以移动范围。在每一步骤中，包含四个选项需要尝试，向上、向下，向左和向右。如果递归中不满足约束条件，则回退。

### 2.4.4 动态规划与贪婪算法

动态规划：
- 求解一个问题的最优解；
- 整体问题的最优解依赖各个子问题的最优解；
- 小问题之间有相互重叠的更小子问题；
- 从上往下分析问题，从下往上求解问题。（**在应用动态规划解决问题的时候，我们总是从解决最小问题开始，并把已经解决的子问题的最优解存储下来，并把子问题的最优解组合起来来逐步解决大的问题。**）

#### 面试题 14：剪绳子(利用额外的数组保存子问题的最优解)
**题目**：给定一根长度为n的绳子，请把绳子剪成m段(m和n都是整数)，每段绳子的长度为k[0],k[1],...,k[m]。请问各个绳子长度连乘最大是多少。

解题思路：利用动态规划来求解。用一个数组来存储计算过程中的子问题的最优解。
设计目标函数f(n)=max(f(i)*f(n-i)),我们求该目标函数的最大值即可。
在计算过程中，我们会不断的计算重复的子问题。因此，我们从下往上计算，我们先得到小问题的答案，并保存起来，再逐步解决大问题的答案。

```python
def maxProductAfterCutting(int length):
    if(length<2):
	return 0
    if(length==2):
        return 1
    if(length==3):
        return 2
    products = [0 for _ in range(length+1)]
    prodcuts[0] = 0
    prodcuts[1] = 1
    prodcuts[2] = 2
    prodcuts[3] = 3
    for i in range(4,length+1):
        max = -1
	for j in range(1,i/2+1):
	    score = prodcuts[j]*prodcuts[i-j]
	    if score > max:
	        max = score
	prodcuts[i] = max
    return prodcuts[length]
 ```

#### 附加面试题：连续子数组的最大和（利用额外的数组保存子问题的最优解）
**题目**：输入一个整型数组nums，数组里有正数也有负数。数组中一个或连续的多个整数组成一个子数组。求所有子数组的和的最大值。要求时间复杂度为 O(n)。

解题思路：
可以用动态规划的思想来分析这个问题。如果用函数 f(n)表示以第 n 个数字结尾的子数组的最大和，那么我们需要求出 max[f(n)].

若f(n-1)<=0，则f(n) = nums[n];否则,f(n) = f(n-1) + nums[n].

```python
def findGreatestSumOfSubArray(nums):
    if nums == None or len(nums) == 0:
        return 0;
    curSum = [0 for i in range(len(nums))]
    curSum = nums[0]
    for i in range(len(nums)):
        if(curSum[i-1]<=0):
	    curSum[i] = nums[i]
	else:
	    curSum[i] = curSum[i-1] + nums[i]
    return max(curSum)
 ```


### 2.4.5 位运算
- 与： &
- 或： |
- 异或： ^
- 左移：<<
- 右移：>>
### 面试题：15 二进制中1的个数
**题目**:输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。

解题思路：把一个整数减去1，再和原整数做与运算，会把该整数最右边的1变为0.

```python
def NumberOf1(int n):
    int count = 0
    while(n!=0){
        count += 1
        n = n & (n-1)
    }
    return count
 ```

# 高质量的代码

## 3.1面试官谈代码质量
## 3.2 代码的规范性
- 代码书写清晰
- 代码布局清洗
- 代码明明合理
## 3.3 代码的完整性
- 功能测试（完成基本功能）
- 边界测试（代码中右循环和迭代，结束条件是否正确）
- 负面测试（错误输入）


### 面试题：16
### 面试题：17
### 面试题：18

#### 题目一：

#### 题目二：删除链表中重复的节点

解题思路: 遇到重复的节点，跳过，直到遇见空节点或者不相等节点.
```python
def DeleteDuplication(ListNode pHead):
    if pHead == null or pHead.next == null:
        return pHead
    ListNode curNode = pHead
    ListNode preNode = null
    while(curNode == None or curNode.next == None):
        if(curNode.val != curNode.next.val):
            preNode = curNode
	    curNode = curNode.next
	else:
	    val = curNode.val
	    curNode = curNode.next
	    while(curNode != None and curNode.val == val):
                curNode = curNode.next
	    if preNode == null:
	        pHead = curNode
	    else:
	        preNode.next = curNode
    
    return pHead
 ```

### 面试题：19 正则表达式匹配
**题目**:请实现一个函数用来匹配包括'.'和'*'的正则表达式。模式中的字符'.'表示任意一个字符，而'*'表示它前面的字符可以出现任意次（包含0次）。 在本题中，匹配是指字符串的所有字符匹配整个模式。
例如，字符串"aaa"与模式"a.a"和"ab*ac*a"匹配，但是与"aa.a"和"ab*a"均不匹配.

解题思路：
- 如果模式中的字符ch是“.”，那么可以匹配字符串中任意字符。
- 如果模式中的字符ch不是“.”，而且字符串中的字符也是ch，那么他们互相匹配。
- 如果模式中的下一个字符ch是“*”，则需要考虑下列情况：（1）匹配0次，则字符不动，模式向后移动两位；（2）匹配1次，则字符串向后移动一位，模式向后移动两位；（3）匹配m次，则字符串向后移动一位，模式保持不变。

## 3.4 代码的鲁棒性
提高代码的鲁棒性的有效途径是进行防御性编程。防御性编程指预见在什么地方可能会出现问题，并为这些可能出现的问题制定处理方式。在面试时，最简单也最实用的防御性编程就是在函数入口添加代码以验证用户输入是否符号要求。

### 面试题：23 链表中环的入口节点（快慢指针）
**题目**:如果一个链表中包含环，如何找出环的入口节点？

解题思路：
- 判断是否有环（快指针的速度是慢指针的2倍）
- 计算环长m
- 快指针先走m步；然后快慢指针一起走，相遇时的节点即为入口节点。设总长度为n。（n-m=l，第l个节点即为入口节点）


### 面试题：24 反转列表（多指针，3个指针）
**题目**:定义一个函数，输入一链表的头节点，反转该链表并输出反转后链表的头节点。

解题思路：定义三个指针，即前指针（preNode）指向前一个节点，当前指针（curNode）指向当前节点和后指针（nexNode）指向后一个节点。
反转的过程如下（收敛依据，curNodex！=null）：
- 首先用nexNode保存curNode.next；
- 然后断开连接，curNode.next = preNode;
- 其次反转连接，用preNode保存curNode，preNode=curNode；
- 最后替换curNode，curNode = nexNode.
- 返回preNode；



### 面试题：25 合并两个排序的链表
**题目**:输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序。

例子：
```python
def Merge(head1, head2):
    if(head1 == null)
        return head2
    elif(head2 == null)
        return head1
    mergeNode = None
    if(head1.val <= head2.val)
        mergeNode = head1
	mergeNode.next = Merge(head1.next, head2)
    else
        mergeNode = head2
	mergeNode.next = Merge(head1, head2.next)
    return mergeNode
 ```
### 面试题：26 树的子结构
**题目**:输入两颗二叉树A和B，判断B是不是A的子结构。

解题思路：DFS+BFS。
- 首先利用DFS寻找A和B相等的节点；
- 在找到相等的节点后，利用BFS同时匹配left和right子节点是否相等；

```python
def HasSubtree(head1, head2):
    if head1 == None or head2 == None:
        return false;
    result = False
    if(head1.val == head2.val):
        result = IsSubtree(head1, head2)
    #DFS分别搜索left和right
    if(!result):
        result = HasSubtree(head1.left, head2)
    if(!result):
        result = HasSubtree(head1.right, head2)
    return result

def IsSubtree(head1, head2):
    if(head2 == null)
        return True
    if(head1 == null)
        return False
    if(head1.val == head2.val)
        #BFS同时搜索left和right
	return IsSubtree(head1.left, head2.left) and IsSubtree(head1.right, head2.right)
    return False
 ```
# 解决面试思路
在编程前解释思路。应聘者如果没有想清楚就动手，则本身就不是太好。
## 4.2 画图让抽象问题形象化
有不少与数据结构相关的问题，比如二叉树、二维数组、链表等问题都可以采用画图的方式来分析。

### 面试题：27 二叉树镜像
**题目**:请完成一个函数，输入一颗二叉树，该函数的输出它的镜像。

解题思路：递归地交换左子树和右子树。

```python
def Mirror(root):
    if root == None:
        return
    left = root.left
    right = root.right

    root.left = right
    root.right = left

    if(root.left!=None)
        return Mirror(root.left)
    if(root.right!=None)
        retrun Mirror(root.right)
 ```
 
### 面试题：28 对称二叉树
**题目**:请实现一个函数，用来判断一颗二叉树是不是对称的。
解题思路：
- 前序遍历：先根节点，左节点和右节点；
- 自定义前序遍历：先根节点，右节点和左节点。
通过比较上述两种遍历的节点是否相同，即可判断该二叉树是否为对称二叉树。
```python
def isSymmetrical(root):
    if root == None:
        return True
    return isSymmetricalCore(root1, root2):
def isSymmetricalCore(root1, root2):
    if(root1 == null && root2 == null):
        return True
    if(root1 == null || root2 == null):
        return False
    if(root1.val != root2.val)
        return False
    return isSymmetricalCore(root1.left, root2.right) &&
           isSymmetricalCore(root1.right, root2.left)
 ```
 
### 面试题：29 顺时针打印矩阵
**题目**:输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下矩阵： 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 则依次打印出数字1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10.

解题思路：注意边界条件。

## 4.3 举例让抽象问题具体化
### 面试题：29 顺时针打印矩阵
**题目**:输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下矩阵： 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 则依次打印出数字1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10.

解题思路：注意边界条件。
 
### 面试题：30 包含min函数的栈
**题目**:定义栈的数据结构，请在该类型中实现一个能够得到栈最小元素的min函数。
解题思路：利用辅助stack保存min值。

### 面试题：31 栈的压入、弹出序列
**题目**:输入两个整数序列，第一个序列标识栈的压入顺序，请判断第二个序列是否为该栈的弹出序列。

解题思路：利用辅助stack来模拟压入与弹出。如果下一个弹出数字刚好是栈顶则继续，如果不是则将压入序列中的数字依次压入直到满足栈顶数字与弹出序列相等为止。如果所有数字都压入辅助stack中仍然没有满足条件，则该序列不可能是一个弹出序列。

### 面试题：32 从上到下打印二叉树
**题目**:从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

解题思路：BFS（利用queue先进先出）


### 面试题:33 二叉搜索树的后序遍历序列
**题目**：输入一个正数组，判断该数组是不是某二叉搜索树的后序遍历的结果。

解题思路：在后序遍历中，最后一个节点总是root节点。将整个数组可以划分为两组，一组为root的左子树，在该子树中，所有的节点都是小于root；另一组为root的右子树，在该子树中所有的节点都大于root。用递归的方法可以解决该问题，不断的取数组的最后一位为root，并且不断分割对比。

Trick：如果右子树中存在小于root的节点则直接返回false。


### 面试题:34 二叉树中和为某一值的路径
**题目**：输入一颗二叉树和一个整数，打印出二叉树中节点值的和为输入整数的所有路径。从树的根节点开始往下一直到叶节点所经过的节点形成一条路径。

解题思路：可以利用先序遍历，先跟，后左，再右。创建一个辅助stack用以保存路径，当所走路径满足要求后遍历打印stack中节点的值。记得在利用完节点后，在stack中删除该节点。

### 面试题：55 二叉树的深度
**题目**:输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。

解题思路：分别递归地计算左子树与右子树深度，并且比较两个子树的深度，选择深度较大的为返回值。

```python
def TreeDepth(root):
    if root == None:
        return 0
    leftHigh = TreeDepth(root.left)
    rightHigh = TreeDepth(root.right)
    return leftHigh >= rightHigh : leftHigh + 1 : rightHigh + 1
 ```

```python
def TreeDepth(root):
    if root == None:
        return 0
    leftHigh = TreeDepth(root.left)
    rightHigh = TreeDepth(root.right)
    return leftHigh >= rightHigh : leftHigh + 1 : rightHigh + 1
 ```

