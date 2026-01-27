
# Range Sum Query – Immutable

## 🧩 Problem

Given an integer array `nums`, handle multiple queries of the form  
`sumRange(left, right)` which returns the sum of elements between indices  
`left` and `right` **inclusive**.

The array is **immutable**, meaning it does not change after initialization.

---

## 🧠 Approach

Store the input array internally.  
For each query, iterate from index `left` to `right` (inclusive) and
accumulate the sum of the elements in this range, then return the result.

---
## ✅ Solution (C#)

~~~csharp
public class NumArray {
  //private int [] _array = new int []{};
  private List<int> list= new List<int>();
    public NumArray(int[] nums) {
        for(int i=0 ; i< nums.Length ; i++)
        {
            list.Add(nums[i]);
        }
    }
    
    public int SumRange(int left, int right) {
        int sum =0;
        if(left >= 0 && left <= right && right< list.Count)
        {           
            for(int i=0 ; i < right-left+1 ; i++ )
            {
                sum+= list[left+i] ;
            }      
           return sum;     
        }
        else
        {
            return 0;
        }
    }
}
~~~

### Complexity
- Time Complexity: O(n)
- Space Complexity: O(n)

## Approach 2 — Prefix Sum (Optimized)

Instead of summing the range every time, we calculate cumulative sums once in the constructor.

Each index in the prefix array stores the sum from index 0 up to that index.

To get sum from left to right:
- If left == 0 → return prefix[right]
- Otherwise → return prefix[right] - prefix[left - 1]

### Optimized Solution (C#)

public class NumArray {
    private int[] prefix;

    public NumArray(int[] nums) {
        prefix = new int[nums.Length];
        prefix[0] = nums[0];

        for (int i = 1; i < nums.Length; i++) {
            prefix[i] = prefix[i - 1] + nums[i];
        }
    }

    public int SumRange(int left, int right) {
        if (left == 0) return prefix[right];
        return prefix[right] - prefix[left - 1];
    }
}

### Complexity (Optimized)

Constructor: O(n)  
Each Query: O(1)  
Space: O(n)
