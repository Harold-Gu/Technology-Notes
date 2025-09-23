# Introduce

* An anagram is a word or phrase formed by rearranging the letters of a different word or phrase, using all the original letters exactly once.
* Given an array of strings, group the anagrams together. You can return the result list in any order.
* Input: strs = ["eat", "tea", "tan", "ate", "nat", "bat"] 
  Output: [["bat"], ["nat", "tan"], ["ate", "eat", "tea"]] 
  Explanation:
  * There are no strings in strs that can be formed into "bat" by rearrangement.
  * The strings "nat" and "tan" are anagrams of each other because they can be rearranged to form one another.
  * The strings "ate", "eat" and "tea" are anagrams of each other because they can be rearranged to form one another.

# Answers

## Simpleness

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<String, List<String>>();
        for (String str : strs) {
            char[] array = str.toCharArray();
            Arrays.sort(array);
            String key = new String(array);
            List<String> list = map.getOrDefault(key, new ArrayList<String>());
            list.add(str);
            map.put(key, list);
        }
        return new ArrayList<List<String>>(map.values());
    }
}
```

* Create mapping table: Create a HashMap where the keys are the sorted strings and the values are the lists of anagrams. 
* Traverse the string array: Use the enhanced for loop to traverse each string input. 
* Generate key: For each string, perform the following operations:
  Convert to character array: char[] array = str.toCharArray()
  Sort the character array: Arrays.sort(array)
  Convert the sorted character array back to a string as the key: String key = new String(array)
* Group processing:
  Use the getOrDefault method to obtain the list corresponding to the key. If it does not exist, create a new ArrayList.
  Add the original string to the corresponding list.
  Update the mapping table. 
* Return result: Convert all values (i.e., all groups) in the mapping table into an ArrayList and return it.

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        mp = collections.defaultdict(list)

        for st in strs:
            key = "".join(sorted(st))
            mp[key].append(st)
        
        return list(mp.values())

```

