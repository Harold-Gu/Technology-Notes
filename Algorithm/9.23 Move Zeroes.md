# Move Zeroes

* Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements. 
  Please note that the array must be operated on in place without copying it. 

  Example 1: 
  Input: nums = [0, 1, 0, 3, 12]
  Output: [1, 3, 12, 0, 0] 
  Example 2: 
  Input: nums = [0]
  Output: [0]

## Answers

* Using two pointers, the left pointer points to the tail of the currently processed sequence, while the right pointer points to the head of the sequence to be processed. 
  The right pointer keeps moving to the right. Whenever the right pointer points to a non-zero number, the corresponding numbers at the left and right pointers are swapped, and the left pointer moves to the right. 
  It is noted that the following properties hold: 
  The numbers on the left side of the left pointer are all non-zero. 
  The area to the left of the right pointer up to the left pointer itself is all zero. 
  Therefore, in each swap, the zero at the left pointer is swapped with the non-zero number at the right pointer, and the relative order of the non-zero numbers remains unchanged.

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int n = nums.length, left = 0, right = 0;
        while (right < n) {
            if (nums[right] != 0) {
                swap(nums, left, right);
                left++;
            }
            right++;
        }
    }

    public void swap(int[] nums, int left, int right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
    }
}


```

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        n = len(nums)
        left = right = 0
        while right < n:
            if nums[right] != 0:
                nums[left], nums[right] = nums[right], nums[left]
                left += 1
            right += 1


```

