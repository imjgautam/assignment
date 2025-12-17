---
description: >-
  Write a function to find the longest common prefix string amongst an array of
  strings.  If there is no common prefix, return an empty string "".
---

# Longest Common Prefix

**Example 1:**

<pre class="language-json"><code class="lang-json"><strong>Input: strs = ["flower","flow","flight"]
</strong><strong>Output: "fl"
</strong></code></pre>

**Example 2:**

<pre class="language-json" data-overflow="wrap"><code class="lang-json"><strong>Input: strs = ["dog","racecar","car"]
</strong><strong>Output: ""
</strong><strong>Explanation: There is no common prefix among the input strings.
</strong></code></pre>

&#x20;

**Constraints:**

* `1 <= strs.length <= 200`
* `0 <= strs[i].length <= 200`
* `strs[i]` consists of only lowercase English letters if it is non-empty.



```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        //base condition to check strs should have at leaset one length or should not be 0
        if(strs.length == 0 || strs == null){
            return "";
        }

        // first I will store first string
        String first = strs[0];

        // Now I will make a loop which will only run till the length of first string
        //because first string will act like a longest prefix

        for(int i = 0; i<first.length(); i++){ //flower - 5
            //Now i will take characters one by one from first string
            char currentChar = first.charAt(i); // f
            //now i will add one more loop which will begin from second string of array 
            //till the length of atual array strs
            for(int j = 1; j<strs.length; j++){
                // now i will check from currentChar with the second string chars
                // like currentChar = f ---> second string (flow) char at i is f -- is matching or not
                if(i>=strs[j].length() || currentChar != strs[j].charAt(i)){
                    // if not matching then. I will return the substring till i index only 
                    return first.substring(0, i);
                } 
            }
        }

        //if everything is matched it means my longest prefix will be the first string only
        return first;
    }
}
```
