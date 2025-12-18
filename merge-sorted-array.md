---
description: >-
  You are given two integer arrays nums1 and nums2, sorted in non-decreasing
  order, and two integers m and n, representing the number of elements in nums1
  and nums2 respectively.
---

# Merge Sorted Array

**Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

The final sorted array should not be returned by the function, but instead be _stored inside the array_ `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.

&#x20;

**Example 1:**

<pre class="language-java"><code class="lang-java"><strong>Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
</strong><strong>Output: [1,2,2,3,5,6]
</strong><strong>Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
</strong>The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
</code></pre>

**Example 2:**

<pre class="language-java"><code class="lang-java"><strong>Input: nums1 = [1], m = 1, nums2 = [], n = 0
</strong><strong>Output: [1]
</strong><strong>Explanation: The arrays we are merging are [1] and [].
</strong>The result of the merge is [1].
</code></pre>

**Example 3:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums1 = [0], m = 0, nums2 = [1], n = 1
</strong><strong>Output: [1]
</strong><strong>Explanation: The arrays we are merging are [] and [1].
</strong>The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.
</code></pre>

&#x20;

**Constraints:**

* `nums1.length == m + n`
* `nums2.length == n`
* `0 <= m, n <= 200`
* `1 <= m + n <= 200`
* `-10`<sup>`9`</sup>` ``<= nums1[i], nums2[j] <= 10`<sup>`9`</sup>

&#x20;

**Follow up:** Can you come up with an algorithm that runs in `O(m + n)` time?&#x20;



```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {

        // Input:
        // nums1 = [1,2,3,0,0,0], m = 3
        // nums2 = [2,5,6],       n = 3
        // both arrays are already sorted
        // nums1 has extra space at the end
        // so we will use two pointers + one extra pointer for placement

        int i = m - 1;      // pointer for nums1 valid elements (3 - 1 = 2)
        int j = n - 1;      // pointer for nums2 (3 - 1 = 2)
        int k = m + n - 1;  // pointer to place values inside nums1 (last index)

        // we will compare from the end because
        // placing larger elements at the back avoids overriding values

        while (i >= 0 && j >= 0) {

            // compare last valid elements of nums1 and nums2
            if (nums1[i] > nums2[j]) {

                // nums1[i] is greater
                // so place it at nums1[k]
                nums1[k] = nums1[i];

                // this value is used, move pointer i
                i--;
            } else {

                // nums2[j] is greater or equal
                // place it at nums1[k]
                nums1[k] = nums2[j];

                // this value is used, move pointer j
                j--;
            }

            // k is used, so move it backward
            k--;
        }

        // if nums2 still has remaining elements
        // nums1 elements are already in correct position
        // so we only need to copy remaining nums2 values

        while (j >= 0) {
            nums1[k] = nums2[j];
            k--;
            j--;
        }
    }
}

```
