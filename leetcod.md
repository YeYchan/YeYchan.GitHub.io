#  【数据结构与算法笔记】



# 1.数组

## 1.1删除排序数组中的重复项

给你一个 升序排列 的数组 nums ，请你 原地 删除重复出现的元素，使每个元素 只出现一次 ，返回删除后数组的新长度。元素的 相对顺序 应该保持 一致 。

由于在某些语言中不能改变数组的长度，所以必须将结果放在数组nums的第一部分。更规范地说，如果在删除重复项之后有 k 个元素，那么 nums 的前 k 个元素应该保存最终结果。

将最终结果插入 nums 的前 k 个位置后返回 k 。

不要使用额外的空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成


```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int left=0; //做指针从索引0开始
        int right=1;//右指针从索引1开始
        if(nums.length==1){
            return 1;
        }//如果数组只有一个数,那就返回1就行了
        for(;left<nums.length&&right<nums.length;){
            if(nums[left]==nums[right]){ //如果左右一样那么就让右指针往右移动
                right++;
            }else{
                nums[++left]=nums[right]; //当左右指针所在索引值不一样时,左指针移动享有一位把右指针的值给到左指针
            }
            
        }
        return ++left; //left代表的是索引 数量上要再+1

    }
}
```

## 1.2买卖股票的最佳时机 II

给你一个整数数组 prices ，其中 prices[i] 表示某支股票第 i 天的价格。

在每一天，你可以决定是否购买和/或出售股票。你在任何时候 最多 只能持有 一股 股票。你也可以先购买，然后在 同一天 出售。

返回 你能获得的 最大 利润 。

```java
class Solution {
    public int maxProfit(int[] prices) {
        int min=prices[0]; //把第一天的价格设为最小值
        int sum=0;//利润一开始为0
        for(int i=0;i<prices.length;i++){
            if(prices[i]<min){
                min=prices[i];//如果后一天比前一天的股票价格低,就把最小值变为后一天的
            }else{
                sum+=prices[i]-min;//反之就相减计算利润和
                min=prices[i];//并改变最小值
            }
        }
        return sum; //返回最终利润

    }
}
```
