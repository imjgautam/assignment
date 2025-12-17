---
description: >-
  Given an array of integers nums and an integer target, return indices of the
  two numbers such that they add up to target.
---

# Two Sum

**Example 1:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums = [2,7,11,15], target = 9
</strong><strong>Output: [0,1]
</strong><strong>Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
</strong></code></pre>

**Example 2:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums = [3,2,4], target = 6
</strong><strong>Output: [1,2]
</strong></code></pre>

**Example 3:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums = [3,3], target = 6
</strong><strong>Output: [0,1]
</strong></code></pre>

&#x20;

**Constraints:**

* `2 <= nums.length <= 10`<sup>`4`</sup>
* `-10`<sup>`9`</sup>` ``<= nums[i] <= 10`<sup>`9`</sup>
* `-10`<sup>`9`</sup>` ``<= target <= 10`<sup>`9`</sup>
* **Only one valid answer exists.**

You may assume that each input would have _**exactly**_**&#x20;one solution**, and you may not use the _same_ element twice.

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {

        // HashMap to store key value pair so i will store number -> and its index
        // This helps us find the required complement in O(1) time
        HashMap<Integer, Integer> hm = new HashMap<Integer, Integer>();

        // Step 1: Store each number along with its index in the map
        for (int i = 0; i < nums.length; i++) {
            hm.put(nums[i], i); // 2 -> 0, 7 -> 1 etc
        }

        // Step 2: Traverse the array again to find the pair
        for (int i = 0; i < nums.length; i++) {

            // Calculate the number needed to reach the target
            // x + y = 9 
            // x = 9 - y --> 9 - 2 = 7
            // we need to find x --> 7 in hashmap if matched then we will return their indexes
            int s = target - nums[i];

            // Check:
            // 1. If the required number exists in the map
            // 2. Ensure we are not using the same element twice
            // suppose if there is numbers like [5, 6, 4] and target is 10
            // then 10 -  5 = 5 and five is already in hashmap so thatswhy
            // we need to check the 5 should not repeat twice
            if (hm.containsKey(s) && hm.get(s) != i) {

                // If found, return the current index
                // and the index of the required number
                return new int[] { i, hm.get(s) };
            }
        }

        // If no valid pair is found (this case won't happen
        // as per problem constraints, but added for safety)
        return null;
    }
}

```
