快速选择算法的 Partition 的实质：
快速选择/快速排序中的 partition 是 可左可右 的partition，也就是说，对于nums[i] == pivot 时，这个数字既可以放在左边，也可以放在右边。

为什么这样划分数组呢？
原因是为了避免出现类似 [1,1,1,1,1,1] 的数组中的元素，全部被分到一边的情况。我们让 nums[i] == pivot 的情况既不属于左边也不属于右边，这样就能够让 partition 之后的结果稍微平衡一些。
如果 quick select / quick sort 写成了nums[i] < pivot 在左侧，nums[i] >= pivot 在右侧这种形式，就会导致划分不平均，从而导致错误或者超时。

为什么问题《partition array》不能使用同样的代码？
对于问题《partition array》来说，题目的要求是将数组划分为两个部分，一部分满足一个条件，另外一部分不满足这个条件，所以可以严格的把 nums[i] < pivot 放在左侧，把 nums[i] >= pivot 放在右侧，这样子做完一次 partition 之后，就能够将这两部分分开。

总结
简单的说就是，quick select 和 quick sort 的 partition 目标不是将数组 严格的按照 nums[i] < pivot 和nums[i] >= pivot 去拆分开，而是只要能够让左半部分 <= 右半部分即可。这样子 nums[i] == pivot 放在哪儿都无所谓，两边都可以放。
