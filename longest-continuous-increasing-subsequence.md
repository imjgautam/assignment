---
description: >-
  Given an unsorted array of integers nums, return the length of the longest
  continuous increasing subsequence (i.e. subarray). The subsequence must be
  strictly increasing.
---

# Longest Continuous Increasing Subsequence

A **continuous increasing subsequence** is defined by two indices `l` and `r` (`l < r`) such that it is `[nums[l], nums[l + 1], ..., nums[r - 1], nums[r]]` and for each `l <= i < r`, `nums[i] < nums[i + 1]`.

&#x20;

**Example 1:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums = [1,3,5,4,7]
</strong><strong>Output: 3
</strong><strong>Explanation: The longest continuous increasing subsequence is [1,3,5] with length 3.
</strong>Even though [1,3,5,7] is an increasing subsequence, it is not continuous as elements 5 and 7 are separated by element
4.
</code></pre>

**Example 2:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums = [2,2,2,2,2]
</strong><strong>Output: 1
</strong><strong>Explanation: The longest continuous increasing subsequence is [2] with length 1. Note that it must be strictly
</strong>increasing.
</code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 10`<sup>`4`</sup>
* `-10`<sup>`9`</sup>` ``<= nums[i] <= 10`<sup>`9`</sup>

```java
class Solution {
    public int findLengthOfLCIS(int[] nums) {
        int count = 1; // initial count and also used to store the max sequence length
        int resetCount = 1; // current increasing sequence length inside the loop
        // base case but not necessary according to Constraints
        if(nums.length == 0){
            return count-1;
        }
        for (int i = 1; i < nums.length; i++) {

            // sequence increasing 
            if (nums[i] > nums[i - 1]) {
                resetCount++;
                count = Math.max(count, resetCount); // compare the max and set the new max to count
            } else {
                // sequence break and reset to 1
                resetCount = 1;
            }
        }

        return Math.max(count, resetCount); // return the max count
    }
}
```
