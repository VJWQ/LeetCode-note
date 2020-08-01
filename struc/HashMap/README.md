# 哈希表

|       Java        |      C++      | Python |
|   -------------   | ------------- | ------ |
| HashSet / HashMap | unordered_map |  dict  |

主要考点：
1. 是否熟练掌握哈希表的基本原理
2. 是否会灵活的使用哈希表解决问题


- **HashSet**实现了Set接口，其内部不允许出现重复的值，如果将一个对象存入HashSet，必须重写equals()和hashCode()方法，这样才能确保集合中不存在同一个元素。HashSet的内部是无序的，因此不能使用 hashset.get(index) 来获取元素。  
- **HashMap**实现了Map接口，其内容是键值对的映射（key->value），不允许出现相同的键（key）。在查询的时候会根据给出的键来查询对应的值。
- 可以认为，HashSet和HashMap增查操作的时间复杂度都是常数级的。    



## 冲突（Collision）：两个不同的 key 经过哈希函数的计算后，得到了两个相同的值。  
解决冲突的方法主要有两种：
- **开散列法**（Open Hashing）：哈希表所基于的数组中，每个位置是一个 Linked List 的头结点。这样冲突的 <key, value> 二元组，就都放在同一个链表中。
- **闭散列法**（Closed Hashing）：在发生冲突的时候，后来的元素，往下一个位置去找空位。
