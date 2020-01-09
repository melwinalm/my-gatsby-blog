---
title: Find intersection of two unsorted arrays
date: "2020-01-08"
type: problem-solving
description: Find intersection of two unsorted arrays
tags: csharp
---

Note: This problem was taken from LeetCode - [Intersection of two arrays -2](https://leetcode.com/problems/intersection-of-two-arrays-ii/submissions/)

##### Naive Approach

The brute force way to solve this problem is loop through every element of the first array and check if it exists in the second array.

```csharp
public int[] Intersect(int[] nums1, int[] nums2) {
      List<int> intersection = new List<int>();
      
      for (int i = 0 ; i < nums1.Length ; i++){
          if(nums2.Contains(nums1[i])){
              intersection.Add(nums1[i]);
          }
      }
      
      return intersection.ToArray();
  }
```

Time complexity - O(m * n) where m and n are size of the two arrays

The above solution works in most of the cases, but fails during some of the cases. Suppose the arrays are [1,1] and [1] then the expected output is [1] but the above code returns [1,1].

Lets try a more time-efficient and fool proof solution.

##### Two Pointer Approach

In this approach we will have two pointers (i.e. array index pointers) and loop through the sorted arrays.

```csharp
public int[] Intersect(int[] nums1, int[] nums2) {
    List<int> intersection = new List<int>();
    
    // Initialize both the pointers to zero
    int pt1 = 0;
    int pt2 = 0;
    
    // Sort both the arrays
    Array.Sort(nums1); // O(nlogn)
    Array.Sort(nums2); // O(mlogm)
    
    while(true){ // O(m+n)
        // breaks the while loop if the any one of the array pointer exceeds the array boundary
        if(pt1 > nums1.Length - 1 || pt2 > nums2.Length - 1){
            break;
        }
        
        if(nums1[pt1] < nums2[pt2]){
            pt1++;
        }
        else if (nums1[pt1] > nums2[pt2]){
            pt2++;
        }
        else{
            intersection.Add(nums1[pt1]);
            pt1++;
            pt2++;
        }
    }
    return intersection.ToArray();
}
```

In the above solution, I am sorting both the arrays first and then using the two-pointer technique to find the intersection. Total time complexity is O(nlogn) + O(mlogm) + O(m+n)

##### Dictionary Approach (Best Solution)

In this approach, loop through the one of the array and add them to a dictionary along with the count. Then loop again through the second array along with decrementing the count. At the end tou will get the intersection of the two arrays.

```csharp
public int[] Intersect(int[] nums1, int[] nums2) {
    Dictionary<int, int> count = new Dictionary<int,int>();
    List<int> intersection = new List<int>();
    
    for (int i = 0; i < nums1.Length; i++){
        // If the number already exists then increment it by one
        if (count.ContainsKey(nums1[i])){
            
            count[nums1[i]] += 1;
        }
        else{
            count[nums1[i]] = 1;
        }
    }
    
    for (int i = 0 ; i < nums2.Length; i++){
      // If the key exists then decrement the count and add it to the intersection array
        if (count.ContainsKey(nums2[i]) && count[nums2[i]] > 0){
            intersection.Add(nums2[i]);
            count[nums2[i]] -= 1;
        }
    }
    
    return intersection.ToArray();
}
```

The dictionary based approach is the fastest among the all, since this approach doesn't require the arrays to be sorted. The total time complexity of this approach is O(m + n) where m and n are the size of the arrays.

##### Follow up questions from Leetcode
- What if the given array is already sorted? How would you optimize your algorithm?

You could use dictionary or two pointer approach if the arrays are already sorted, since both will give a time complexity of O(m+n). But out of these two methods two pointer method is the best since dictionary approach requires extra space to store dictionary data.

- What if nums1's size is small compared to nums2's size? Which algorithm is better?
- What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?
