---
description: >-
  Given an integer array nums sorted in non-decreasing order, remove the
  duplicates in-place such that each unique element appears only once. The
  relative order of the elements should be kept the same.
---

# Remove Duplicates from Sorted Array

Consider the number of _unique elements_ in `nums` to be `k`**`​​​​​​​`**&#x200B;​​​​​​. After removing duplicates, return the number of unique elements `k`.

The first `k` elements of `nums` should contain the unique numbers in **sorted order**. The remaining elements beyond index `k - 1` can be ignored.

**Custom Judge:**

The judge will test your solution with the following code:

```
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be **accepted**.

&#x20;

**Example 1:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums = [1,1,2]
</strong><strong>Output: 2, nums = [1,2,_]
</strong><strong>Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
</strong>It does not matter what you leave beyond the returned k (hence they are underscores).
</code></pre>

**Example 2:**

<pre class="language-json"><code class="lang-json"><strong>Input: nums = [0,0,1,1,1,2,2,3,3,4]
</strong><strong>Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
</strong><strong>Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
</strong>It does not matter what you leave beyond the returned k (hence they are underscores).
</code></pre>

&#x20;

**Constraints:**

* `1 <= nums.length <= 3 * 10`<sup>`4`</sup>
* `-100 <= nums[i] <= 100`
* `nums` is sorted in **non-decreasing** order.

```java
class Solution {
    public int removeDuplicates(int[] nums) {

        // Step 1: Identify the pattern
        // Since the array is already sorted, duplicates will be next to each other
        // So the best approach here is using TWO POINTERS

        // Step 2: Confirm constraints
        // We are allowed to modify the existing array
        // So we can use one pointer to READ values
        // and one pointer to WRITE unique values

        int i = 0; 
        // Pointer i:
        // This pointer keeps track of the position where the next unique element
        // should be placed. It also helps us calculate the count of unique elements.

        // Pointer j will start from index 1
        // It will read the array and compare values
        for (int j = 1; j < nums.length; j++) {

            // If current element is NOT equal to the last unique element
            // Example: [1,1,3,3]
            if (nums[i] != nums[j]) {

                // Move i forward because we found a new unique value
                i++;

                // Place the new unique value at index i
                // Explanation:
                // When nums[i] == nums[j] (like 1 == 1), we skip it
                // j moves ahead
                // When nums[i] != nums[j] (1 != 3),
                // we overwrite nums[i] with nums[j]
                // so now index i contains the next unique value
                nums[i] = nums[j];
            }
        }

        // i represents the last index of unique elements
        // Since index starts from 0, total unique elements = i + 1
        return i + 1;
    }
}

```
