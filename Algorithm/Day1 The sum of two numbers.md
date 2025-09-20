# Introduce

* Given an integer array `nums` and an integer target value `target`, please find the two integers in the array whose sum is equal to the target value `target`, and return their array indices. 
  You can assume that each input will correspond to only one answer, and you cannot use the same element twice. 
  You can return the answers in any order.

## Answers

### Simpleness

* java

  ```java
  class Solution {
      public int[] twoSum(int[] nums, int target) {
          int n = nums.length;
          for (int i = 0; i < n; ++i) {
              for (int j = i + 1; j < n; ++j) {
                  if (nums[i] + nums[j] == target) {
                      return new int[]{i, j};
                  }
              }
          }
          return new int[0];
      }
  }
  
  ```

  * To get the length of the array: int n = nums.length; Get the length of the input array nums.
  * Two nested loops: Use two for loops to traverse all pairs of elements in the array:
    The outer loop variable i ranges from 0 to n-1, representing the index of the first element.
    The inner loop variable j ranges from i+1 to n-1, representing the index of the second element (j > i ensures that each pair of elements is checked only once).
  * Condition check: if (nums[i] + nums[j] == target) checks whether the sum of the current two elements is equal to the target value target. 
  * If a pair of elements that meet the conditions is found, immediately return a new array containing the indices of these two elements, new int[]{i, j}. 
  * If no solution that meets the conditions is found after traversing all pairs of elements, return an empty array new int[0].

* python

  ```python
  class Solution:
      def twoSum(self, nums: List[int], target: int) -> List[int]:
          n = len(nums)
          for i in range(n):
              for j in range(i + 1, n):
                  if nums[i] + nums[j] == target:
                      return [i, j]
          
          return []
  
  ```

  * First, get the length of the array: n = len(nums)
  * Use two nested loops to traverse all possible pairs of elements

  - The outer loop traverses the first element with index i (from 0 to n-1)
  - The inner loop traverses the second element with index j (from i+1 to n-1) to ensure no duplicate pairs are calculated
  - Check if the sum of the current pair of elements equals the target value: if nums[i] + nums[j] == target
  - If a pair that meets the condition is found, immediately return their indices: return [i, j]
  - If no pair is found after traversing all elements, return an empty array: return []

### Harder

* python

  * ```python
    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
            hashtable = dict()
            for i, num in enumerate(nums):
                if target - num in hashtable:
                    return [hashtable[target - num], i]
                hashtable[nums[i]] = i
            return []
    
    
    ```

  * Hash Table Initialization : Creates an empty dictionary hashtable to store elements and their indices

  * Single Pass Through Array : Uses enumerate() to iterate through the array, getting both the index i and value num of each element

  * Check Complement : For each element, calculates target - num (the complement needed to reach the target) and checks if this complement exists in the hash table

  * If the complement exists, returns a list containing the index of the complement (from the hash table) and the current index i

  * If the complement doesn't exist, adds the current element and its index to the hash table

  * No Solution Case : If no valid pair is found after iterating through the entire array, returns an empty list
