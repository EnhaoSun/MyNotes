# 方法
## 递归（Recursive）
**递归的本质是把一个问题分解成两个或多个小问题**  
优点：简洁  
缺点：每一次函数调用，都需要在内存栈中分配空间以保存参数，返回地址及临时变量，而且往栈理压如数据和弹出数据都需要时间。
另外，递归中有可能很多计算都是重复的，从而对性能带来很大的负面影响。



# 经典问题

## Top K

* https://juejin.im/entry/5c565fb7f265da2d84105958
* https://blog.csdn.net/believe__sss/article/details/79061532



# 数据结构

## 树

### 平衡树

* [https://zh.wikipedia.org/wiki/%E5%B9%B3%E8%A1%A1%E6%A0%91](https://zh.wikipedia.org/wiki/平衡树)

### 红黑树

* [https://zh.wikipedia.org/wiki/%E7%BA%A2%E9%BB%91%E6%A0%91](https://zh.wikipedia.org/wiki/红黑树)

### 二叉搜索树

* [https://zh.wikipedia.org/zh-cn/%E4%BA%8C%E5%85%83%E6%90%9C%E5%B0%8B%E6%A8%B9](https://zh.wikipedia.org/zh-cn/二元搜尋樹)

## 哈希函数

### 哈希冲突

解决哈希冲突的方法

* 开放寻址法：遇到冲突时，寻找其他空位
* 链表法： 在冲突的位置，向数组元素（Entry）插入链表节点