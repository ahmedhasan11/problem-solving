# Two Sum

## Problem
Two Sum
Given an array of integers nums and an integer target, return the indices i and j such that nums[i] + nums[j] == target and i != j.

You may assume that every input has exactly one pair of indices i and j that satisfy the condition.

Return the answer with the smaller index first.

---

## Examples

### Example 1

Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]

### Example 2

Input: nums = [4,5,6], target = 10

Output: [0,2]
---

## Approach
While iterating through the array, for each number we calculate its complement
(`target - currentNumber`).  
If the complement already exists in a dictionary, we return both indices.  
Otherwise, we store the current number with its index in the dictionary.

## Solution (C#)
~~~csharp
public class Solution {
    public int[] TwoSum(int[] nums, int target) {        
        
        Dictionary<int,int> dict = new Dictionary<int,int>();
        for(int i=0 ; i < nums.Length ; i++)
        {
            int difference= target - nums[i];
            if(dict.ContainsKey(difference))
            {
                if(i< dict[difference])
                {
                return new int [] {i, dict[difference]};
                }
                else
                {
                return new int [] {dict[difference], i};
                }

            }else
            {
            dict.Add(nums[i],i);
            }
        }
         return new int [0] ;   
    }
}

~~~


### Complexity
- Time Complexity: O(n)
- Space Complexity: O(n)

