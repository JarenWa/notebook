
<p style="font-size:30px;">代码随想录学习笔记</p>
<p style="font-size:20px;">目录</p>
<!-- TOC -->

- [二叉树](#二叉树)
    - [1 二叉树理论基础](#1-二叉树理论基础)
    - [2 二叉树递归遍历](#2-二叉树递归遍历)
    - [3 二叉树迭代遍历](#3-二叉树迭代遍历)
    - [Java String类](#java-string类)
    - [Java StringBuffer 和 StringBuilder 类](#java-stringbuffer-和-stringbuilder-类)
    - [Arrays 工具类](#arrays-工具类)
    - [1 回溯算法理论基础](#1-回溯算法理论基础)
    - [x 组合](#x-组合)
    - [4 组合总和III](#4-组合总和iii)
        - [实现1](#实现1)
    - [7 组合总和](#7-组合总和)
- [2 贪心算法](#2-贪心算法)
    - [2 分发饼干](#2-分发饼干)
        - [实现1（时间复杂度太高）](#实现1时间复杂度太高)
        - [实现2](#实现2)

<!-- /TOC -->


# 二叉树

## 1 二叉树理论基础
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
```
## 2 二叉树递归遍历
二叉树前序遍历递归写法
* 确定单层逻辑
* 确定参数、返回值
* 确定终止条件： 没写终止条件或者终止条件写的不对，通常会有栈溢出。操作系统也是用一个栈的结构来保存每一层递归的信息，如果递归没有终止，操作系统的内存栈必然就会溢出。
```
class Solution {
    List<Integer> result = new ArrayList<>();
    public List<Integer> preorderTraversal(TreeNode root) {
        preorder(root);
        return result;
    
    }
    void preorder(TreeNode root){
        if(root != null){
            result.add(root.val);
            preorder(root.left);
            preorder(root.right);
        }
    }
}
```
递归的实现就是：每一次递归调用都会把函数的局部变量、参数值和返回地址等压入调用栈中，然后递归返回的时候，从栈顶弹出上一次递归的各项参数，所以这就是递归为什么可以返回上一层位置的原因。

那我们手动用栈，也可实现遍历。

## 3 二叉树迭代遍历

迭代遍历和递归不一样

前中后序不能简单套用（访问的顺序和元素处理顺序不一致）


<h1 id="0.1"> 补充1</h1>
<a href ="https://www.runoob.com/java/java-string.html" targrt="_blank">见教程</a><br>

## Java String类 

## Java StringBuffer 和 StringBuilder 类

## Arrays 工具类


<h1 id="1"> 回溯算法</h1>
递归函数的参数和返回值<br>
确定终止条件<br>
单层递归逻辑<br>

## 1 回溯算法理论基础
一种搜索方法。回溯是递归的副产品，只要有递归就会有回溯。

回溯法，一般可以解决如下几种问题：

* 组合问题：N个数里面按一定规则找出k个数的集合
* 切割问题：一个字符串按一定规则有几种切割方式
* 子集问题：一个N个数的集合里有多少符合条件的子集
* 排列问题：N个数按一定规则全排列，有几种排列方式
* 棋盘问题：N皇后，解数独等等

```
void backtracking(参数) {
    if (终止条件) {
        存放结果;
        return;
    }

    for (选择：本层集合中元素（树中节点孩子的数量就是集合的大小）) {
        处理节点;
        backtracking(路径，选择列表); // 递归
        回溯，撤销处理结果
    }
}
```

## x 组合
<a href="https://leetcode.cn/problems/combinations/" target="_blank">力扣</a> <br>


## 4 组合总和III
<a href="https://leetcode.cn/problems/combination-sum-iii/" target="_blank">力扣</a> <br>
### 实现1
沿用前面的方法，数字1-9,找k个数字（不重复）的组合，求和等于n的才进入返回结果。


## 7 组合总和

<a href="https://leetcode.cn/problems/combination-sum/" target="_blank">力扣</a>

思考：如何实现重复使用每个候选元素，如何保证组合结果不重复？
```
class Solution {
    List<List<Integer>> result = new ArrayList<>();
    LinkedList<Integer> path = new LinkedList<>(); 

    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        solution(candidates, target, 0, 0);
        return result;
    }
    public void solution(int[] candidates, int target, int sum, int start){
        if(sum > target){
            return;
        }
        if(sum == target){
            result.add(new ArrayList<>(path));
            return;
        }
        for(int i = start ;i< candidates.length;i++){
            path.add(candidates[i]);
            sum += candidates[i];
            solution(candidates, target,sum, i);
            sum -= candidates[i];
            path.removeLast();
        }
    }
   
}
```



# 2 贪心算法

## 2 分发饼干
<a href="https://leetcode.cn/problems/assign-cookies/description/" target="_blank">力扣</a>
### 实现1（时间复杂度太高）
对`s[]`进行升序排序<br>
遍历`g[]`，对于`g[i]`，将与`s[]`中的元素从小到大进行对比，判断能否获得饼干
```
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        int sum = 0;
        for(int i = 0; i < s.length; i++ ){
            for(int j = 1; j < s.length - i; j++){
                if(s[j] < s[j - 1]){
                    int temp = s[j];
                    s[j] = s[j - 1];
                    s[j - 1] = temp;
                }
            }
        }
        for(int i = 0; i < g.length;i++){
            for(int j = 0; j < s.length; j++){
                if(s[j] >= g[i]){
                    sum++;
                    s[j] = 0;
                    break;
                }
            }

        }

        return sum;
    }
}
```

### 实现2
实现1在判断过程中，使用了双层`for`循环，考虑优化。<br>
实现1的排序算法时间复杂度 <em>O(n<sup>2</sup>)</em> 也要优化，`Arrays.sort()`时间复杂度为 <em>O(nlogn) </em>。<br>

优先考虑饼干：
```
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        int sum = 0;
        Arrays.sort(s);
        Arrays.sort(g);
        for(int i = 0, j = 0; i < s.length && j < g.length;i++){
            if(s[i] >= g[j]){
                sum++;
                j++;
            }
        }
        return sum;
    }
}
```

