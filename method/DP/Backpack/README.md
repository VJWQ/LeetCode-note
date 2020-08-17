# A review of classic Backpack problems
* [Backpack I](#Backpack-I): Given `n` items with size `A[i]`, and a backpack with size `m`. How full you can fill this backpack?   
`Each item may only be used once`

* [Backpack II](#Backpack-II): Given `n` items with size `A[i]` and value `V[i]`, and a backpack with size `m`. What's the maximum value can you put into the backpack?
`Each item may only be used once`

* [Backpack III](#Backpack-III): Given `n` kind of items with size `A[i]` and value `V[i]`, and a backpack with size `m`. What's the maximum value can you put into the backpack?  
`Each item may be chosen unlimited number of times`


* [Backpack IV](#Backpack-IV): Given `n` items with size `nums[i]` which an integer array and all positive numbers, **no duplicates**. An integer `target` denotes the size of a backpack. Find the number of possible fill the backpack.  
`Each item may be chosen unlimited number of times`

* [Backpack V](#Backpack-V): Given `n` items with size `nums[i]` which an integer array and all positive numbers. An integer `target` denotes the size of a backpack. Find the number of possible fill the backpack.  
`Each item may only be used once`  

* [Backpack VI](#Backpack-VI): Given an integer array `nums` with all positive numbers and no duplicates, find the number of possible combinations that add up to a positive integer `target`.  
`Each item may be chosen unlimited number of times`  
  



# Classic blog articles: 
## [背包九讲](https://anivian.github.io/pack-master/V2.pdf)
## [背包六问 (in Java)](https://segmentfault.com/a/1190000006325321)

|                                     Problem                                         |    Constraints    |
| ----------------------------------------------------------------------------------- | ----------------- |
| [92. Backpack I](https://www.lintcode.com/problem/backpack/description)             | 单次选择 + 最大体积 |
| [125. Backpack II](https://www.lintcode.com/problem/backpack-ii/description)        | 单次选择 + 最大价值 |
| [440. Backpack III](https://www.lintcode.com/problem/backpack-iii/description)      | 重复选择 + 最大价值 |
| [562. Backpack IV](https://www.lintcode.com/problem/backpack-iv/description)        | 重复选择 + 唯一排列 + 装满方案数 |
| [563. Backpack V](https://www.lintcode.com/problem/backpack-v/description)          | 单次选择 + 装满方案数 |
| [564. Backpack VI](https://www.lintcode.com/problem/combination-sum-iv/description) | 重复选择 + 不同排列 + 装满方案数 |  
   
    
# Backpack I: 01背包问题
内循环逆向更新一维数组

# Backpack II: 完全背包问题
内循环正向更新一维数组

# Backpack III: 背包问题

# Backpack IV: 

# Backpack V: 

# Backpack VI: 



给出 n 个物品, 以及一个数组, nums[i]代表第i个物品的大小, 保证大小均为正数并且没有重复, 正整数 target 表示背包的大小, 找到能填满背包的方案数。
每一个物品可以使用无数次

给出 n 个物品, 以及一个数组, nums[i] 代表第i个物品的大小, 保证大小均为正数, 正整数 target 表示背包的大小, 找到能填满背包的方案数。
每一个物品只能使用一次

给出一个都是正整数的数组 nums，其中没有重复的数。从中找出所有的和为 target 的组合个数。

