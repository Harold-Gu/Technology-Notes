# Sum of Three Numbers

## Introduce

Given an integer array `nums`, determine if there exists a triplet `[nums[i], nums[j], nums[k]]` where `i != j`, `i != k`, and `j != k`, and also `nums[i] + nums[j] + nums[k] == 0`. Please return all unique triplets that sum to zero. 
Please provide the text you want to be translated into English. Without the source text, I am unable to provide a translation.

## Answer

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        int n = nums.length;
        Arrays.sort(nums);
        List<List<Integer>> ans = new ArrayList<List<Integer>>();
        
        for (int first = 0; first < n; ++first) {
            
            if (first > 0 && nums[first] == nums[first - 1]) {
                continue;
            }
            
            int third = n - 1;
            int target = -nums[first];
            
            for (int second = first + 1; second < n; ++second) {
                
                if (second > first + 1 && nums[second] == nums[second - 1]) {
                    continue;
                }
                
                while (second < third && nums[second] + nums[third] > target) {
                    --third;
                }
                
                if (second == third) {
                    break;
                }
                if (nums[second] + nums[third] == target) {
                    List<Integer> list = new ArrayList<Integer>();
                    list.add(nums[first]);
                    list.add(nums[second]);
                    list.add(nums[third]);
                    ans.add(list);
                }
            }
        }
        return ans;
    }
}

```

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        nums.sort()
        ans = list()
        
  
        for first in range(n):
     
            if first > 0 and nums[first] == nums[first - 1]:
                continue
            
            third = n - 1
            target = -nums[first]
            
            for second in range(first + 1, n):
                
                if second > first + 1 and nums[second] == nums[second - 1]:
                    continue
                
                while second < third and nums[second] + nums[third] > target:
                    third -= 1
                
                if second == third:
                    break
                if nums[second] + nums[third] == target:
                    ans.append([nums[first], nums[second], nums[third]])
        
        return ans

```

