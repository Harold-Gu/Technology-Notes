# Longest Consecutive Sequence

Given an unsorted integer array nums, find the length of the longest consecutive sequence (the sequence elements do not have to be consecutive in the original array). 
Please design and implement an algorithm with a time complexity of O(n) to solve this problem.

* Input: nums = [100,4,200,1,3,2]
  Output: 4
  Explanation: The longest consecutive sequence is [1, 2, 3, 4]. Its length is 4. 
  Example 2: 
  Input: nums = [0,3,7,2,5,8,4,6,0,1]
  Output: 9
  Example 3: 
  Input: nums = [1, 0, 1, 2]
  Output: 3

## Answers

### simpleness

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> num_set = new HashSet<Integer>();
        for (int num : nums) {
            num_set.add(num);
        }

        int longestStreak = 0;

        for (int num : num_set) {
            if (!num_set.contains(num - 1)) {
                int currentNum = num;
                int currentStreak = 1;

                while (num_set.contains(currentNum + 1)) {
                    currentNum += 1;
                    currentStreak += 1;
                }

                longestStreak = Math.max(longestStreak, currentStreak);
            }
        }

        return longestStreak;
    }
}


```

* 1. Create a HashSet to store all the numbers in the array. 
  2. Initialize the length of the longest consecutive sequence to 0. 
  3. Traverse each number in the set. 
  4. Only process the starting point of the consecutive sequence (that is, the previous number of the current number is not in the set). 
  5. Search backward for consecutive numbers. 
  6. Update the length of the longest consecutive sequence. 
  7. Return the length of the longest consecutive sequence.

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        longest_streak = 0
        num_set = set(nums)

        for num in num_set:
            if num - 1 not in num_set:
                current_num = num
                current_streak = 1

                while current_num + 1 in num_set:
                    current_num += 1
                    current_streak += 1

                longest_streak = max(longest_streak, current_streak)

        return longest_streak
```

