# The container that holds the most water.

## Introduce

Given an integer array `height` of length `n`, there are `n` vertical lines, where the two endpoints of the `i`-th line are `(i, 0)` and `(i, height[i])`. 
Find two lines such that together with the x-axis they form a container that can hold the most water. 
Return the maximum amount of water that the container can hold.

## Answer

* At this point, we need to move a pointer. Which one should we move? Intuition tells us that we should move the pointer corresponding to the smaller number (that is, the left pointer at this moment). This is because, since the amount of water it can hold is determined by 
  The smaller value among the two pointed numbers multiplied by the distance between the pointers determines it. If we move the pointer with the larger number, then the former "the smaller value among the two pointed numbers" will not increase, while the latter "the distance between the pointers" will decrease, and thus this product will decrease. Therefore, it is unreasonable to move the pointer with the larger number. Therefore, we move the pointer with the smaller number.

```java
public class Solution {
    public int maxArea(int[] height) {
        int l = 0, r = height.length - 1;
        int ans = 0;
        while (l < r) {
            int area = Math.min(height[l], height[r]) * (r - l);
            ans = Math.max(ans, area);
            if (height[l] <= height[r]) {
                ++l;
            }
            else {
                --r;
            }
        }
        return ans;
    }
}

```

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l, r = 0, len(height) - 1
        ans = 0
        while l < r:
            area = min(height[l], height[r]) * (r - l)
            ans = max(ans, area)
            if height[l] <= height[r]:
                l += 1
            else:
                r -= 1
        return ans


```

