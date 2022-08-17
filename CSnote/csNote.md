# CS Note

## Array
### sliding window
For subarray/stirng that satisfies certain requirment

```java
// LC3

class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> map = new HashMap<>();
        int slow = 0, fast = 0;
        int n = s.length();
        int res = 0;
        while(fast < n) {
            char cur = s.charAt(fast);
            map.put(cur, map.getOrDefault(cur, 0) + 1);
            while (map.get(cur) > 1) {
                char slowChar = s.charAt(slow);
                if (map.get(slowChar) == 1) {
                    map.remove(slowChar);
                }else {
                    map.put(slowChar, map.get(slowChar) - 1);
                }
                slow++;
            }
            res = Math.max(res, fast - slow + 1);
            fast++;
        }
        return res;
    }
}
```

### two pointers
[LC75 sort colors](https://leetcode.com/problems/sort-colors/)

maybe 3 pointers

[LC647 Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)

maybe dp

[LC88 merge sorted array](https://leetcode.com/problems/merge-sorted-array/)

maybe 2 pointers in seperate array

### traverse from right
Usually, use this tech with monotonic stack

```java
// monotonic stack
for (int i = n - 1; i >= 0; i++) {
    int cur = arr[i];
    int record = 0;
    while (!stk.isEmpty() && stk.peek() <= cur) {
        stk.pop();
        record++;
    }
    //do something;
    stk.push(cur);
}
 
```