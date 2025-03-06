# leetcode


# [1. Two Sum](https://leetcode.com/problems/two-sum/)

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

**Constraints:**

- `2 <= nums.length <= 10^4`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`
- **Only one valid answer exists.**

**Follow-up:** Can you come up with an algorithm that is less than `O(n^2)` time complexity?

## Solutions
### [Brute Force](./TwoSum.java)

Idea: Select `x` in array and try to find `target - x` in the array.

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++)
            for (int j = i + 1; j < nums.length; j++)
                if (nums[i] + nums[j] == target)
                    return new int[]{i, j};
        return new int[]{};
    }
}
```

Complexity Analysis:

- Time Complexity: $O(n^2)$. $n$ is the number of the elements. The worse case is every element needs to be match once.
- Space Complexity: $O(1)$.

### [Hash Table](./TwoSum2.java)

Idea: Optimize the time complexity of finding `target - x`. Create a hash table using `target - x` as the key and `index` as the value to enhance the speed of finding `target - x`.

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> hashtable = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (hashtable.containsKey(target - nums[i]))
                return new int[]{hashtable.get(target - nums[i]), i};
            hashtable.put(nums[i], i);
        }
        return new int[]{};
    }
}
```

Complexity Analysis:

- Time Complexity: $O(n)$. We use $O(1)$ to find `target - x`.
- Space Complexity: $O(n)$. The main space is used by hash table.
