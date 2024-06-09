用Java刷算法题的常用数据结构

---
Deque<Integer> stack = new LinkedList<>();

栈和队列都可以用ArrayDeque实现

---
【有用】Java刷题常用数据结构和类型转化方法总结<https://blog.csdn.net/blueblueskyz/article/details/114639012>


Java 中的 length属性是针对数组说的,比如说你声明了一个数组,想知道这个数组的长度则用到了 length 这个属性.Java 中的 length() 方法是针对字符串说的,如果想看这个字符串的长度则用到 length() 这个方法.Java 中的 size() 方法是针对泛型集合说的,如果想看这个泛型有多少个元素,就调用此方法来查看!





# 字符串处理

## String

## StringBuilder


# Collection 接口
## List 接口

## Set接口(注重独一无二的性质): 存储的元素不可重复的。
### TreeSet
基于红黑树实现，支持有序性操作，例如根据一个范围查找元素的操作。但是查找效率不如 HashSet，HashSet 查找的时间复杂度为 O(1)，TreeSet 则为 O(logN)。

### HashSet
基于哈希表实现，支持快速查找，但不支持有序性操作。并且失去了元素的插入顺序信息，也就是说使用 Iterator 遍历 HashSet 得到的结果是不确定的。

### LinkedHashSet
具有 HashSet 的查找效率，且内部使用双向链表维护元素的插入顺序。


## Queue接口(实现排队功能的叫号机)
### LinkedList
可以用它来实现双向队列。

### PriorityQueue （功能强大）
<https://blog.csdn.net/u010675669/article/details/86503464>
基于堆结构实现，可以用它来实现优先队列。优先队列的作用是能保证每次取出的元素都是队列中权值最小的(默认：按照本来的顺序不变)(Java的优先队列每次取最小元素，C++的优先队列每次取最大元素)，可以指定排序方式。实现时间复杂度 O(log(n))

Java优先队列PriorityQueue使用详解<https://blog.csdn.net/qq_22596931/article/details/110421457>

```
PriorityQueue <Integer> pq = new PriorityQueue<>();

Queue <Integer> pq = new PriorityQueue<>();
```
```

升序，按照参数数组的下标 0 的元素比较，poll 出来由小到大。o2 - o1 反之。
PriorityQueue<int[]> pq = new PriorityQueue<>((o1, o2) -> o1[0] - o2[0]);
```


# Map


## 常用 HashMap
Map<String, Integer> map = new HashMap<>();

[Java8 map.getOrDefault()你真的了解吗](https://blog.csdn.net/weixin_49065828/article/details/130610362)

[Java的Map中的map.keySet()方法](https://blog.csdn.net/zyx_ly/article/details/88877413)