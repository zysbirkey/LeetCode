# 704 Binary Search 二分查找
## 1. 二分的前提条件
（1）有序数组。ordered

（2）无重复。不然下标不唯一

## 2. 二分的两种写法：左闭右闭、左闭右开
- 当l = 0, r = n，r的值在数组中无法取到, while(l < r) 是正确写法
- 当l = 0, r = n - 1，r的值在数组中可以取到, while(l <= r) 是正确写法
- 每次取mid还是取mid加减一 
- 理解后背熟一套模板，不要搞混。

## 3. 二分的本质
根据是否满足题目的条件来缩小答案所在的区间

## 4. 二分的最大优势
其时间复杂度是O(logn)，因此看到有序数组都要第一时间反问自己是否可以使用二分。
## 5. 关于二分mid溢出
mid = (l + r) / 2时，如果l + r 大于 INT_MAX(C++内，就是int整型的上限)，那么就会产生溢出问题（int类型无法表示该数）
所以写成 mid = l + (r - l) / 2或者 mid = l + ((r - l) >> 1) 可以避免溢出问题


? 对于二进制的正数来说，右移x位相当于除以2的x几次方，所以右移一位等于➗2，用位运算的好处是比直接相除的操作快

'''ptyhon
class Solution(object):
    def search(self, nums, target):
        """
        Function: This is a binary search
        Parameters:
            nums: an ordered list of integers with no repetition
            target: int to search
        Return:
            The index of the target if found, otherwise -1.
        """

        # Initialization
        left = 0  # the first index
        right = len(nums) - 1  # the last index

        while left <= right:
            # find the middle index
            middle = (left + right) // 2
            if nums[middle] > target:
                right = middle - 1
            elif nums[middle] < target:
                left = middle + 1
            else:
                return middle

        return -1
'''
