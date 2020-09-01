---
title: Range Sum Query - Mutable
date: "2020-09-01"
type: problem-solving
description: Range Sum Query - Mutable
tags: csharp
---

Note: This problem was taken from LeetCode - [Range Sum Query - Mutable](https://leetcode.com/problems/range-sum-query-mutable/)

### Using Segment Tree

```csharp
public class NumArray {

    int[] tree;
    int n;
    
    public NumArray(int[] nums) {
        n = nums.Length;
        
        if(n > 0){
            tree = new int[2*n];
            this.BuildSegmentTree(nums);
        }
    }
    
    // O(n) time complexity
    private void BuildSegmentTree(int[] nums){
        for(int i = 0, j = n; j < 2*n; i++, j++){
            tree[j] = nums[i];
        }
        
        for(int i = n-1; i > 0; i--){
            tree[i] = tree[2*i] + tree[2*i+1];
        }
    }
    
    // O(log N) time complexity
    public void Update(int i, int val) {
        int pos = i + n;
        tree[pos] = val;
        
        while(pos > 0){
            int left = pos;
            int right = pos;
            
            if(pos % 2 == 0){
                right = pos + 1;
            }
            else{
                left = pos - 1;
            }
            
            tree[pos/2] = tree[left] + tree[right];
            pos /= 2;
        }
    }
    
    // O(log N) time complexity
    public int SumRange(int i, int j) {
        int l = i + n;
        int r = j + n;
        
        int sum = 0;
        
        while(l <= r){
            if(l % 2 == 1){
                sum += tree[l];
                l++;
            }
            if(r % 2 == 0){
                sum += tree[r];
                r--;
            }
            
            l /= 2;
            r /= 2;
        }
        
        return sum;
    }
}
```
