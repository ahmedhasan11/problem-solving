# 1929. Concatenation of Array

## Problem
Contains Duplicate
Given an integer array nums, return true if any value appears more than once in the array, otherwise return false.

---

## Examples

### Example 1
Input: nums = [1, 2, 3, 3]

Output: true

### Example 2
Input: nums = [1, 2, 3, 4]

Output: false
---

## Approach
- Use a HashSet to keep track of elements seen so far.
- Iterate through the array and check if the current element already exists in the set.
- If it exists, return true; otherwise, add it to the set and continue.

## Solution (C#)
~~~csharp
public class Solution {
    public bool hasDuplicate(int[] nums) {
        HashSet<int> hashingtable = new HashSet<int>();
        //hashingtable.Contains(x);
        //hashingtable.Add(x);

        for(int i=0; i< nums.Length ; i++){
            if(hashingtable.Contains(nums[i])){
                return true;
            }
            else
            {
                hashingtable.Add(nums[i]);
            }
        }
          return false;
    }
}
~~~


### Complexity
- Time Complexity: O(n)
- Space Complexity: O(n)

