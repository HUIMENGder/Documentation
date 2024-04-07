### 摩尔投票法

[229. 多数元素 II](https://leetcode.cn/problems/majority-element-ii/)

* 抵消阶段：两个不同投票进行对坑，并且同时抵消掉各一张票，如果两个投票相同，则累加可抵消的次数；
* 基数阶段：在抵消阶段最后得到的抵消计数只要不为 0，那这个候选人是有可能超过一半的票数的，为了验证，则需要遍历一次，统计票数，才可确定。

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> ans = new ArrayList<>();
        if(nums == null || nums.length == 0) return ans;
        int cand1 = nums[0], count1 = 0;
        int cand2 = nums[0], count2 = 0;
        for(int num : nums){
            if(cand1 == num){
                count1 ++;
                continue;
            }
            if(cand2 == num){
                count2 ++;
                continue;
            }
            if(count1 == 0){
                cand1 = num;
                count1 ++;
                continue;
            }
            if(count2 == 0){
                cand2 = num;
                count2 ++;
                continue;
            }
            count1 --;
            count2 --;
        }
        count1 = 0;
        count2 = 0;
        for(int num : nums){
            if(num == cand1) count1 ++;
            else if(num == cand2) count2 ++; // 去除相同结果
        }
        if(count1 > nums.length / 3) ans.add(cand1);
        if(count2 > nums.length / 3) ans.add(cand2);
        return ans;
    }
}
```

