---
title: Maximum XOR of Two Numbers in an Array
date: "2020-09-02"
type: problem-solving
description: Maximum XOR of Two Numbers in an Array
tags: csharp
---

Note: This problem was taken from LeetCode - [Maximum XOR of Two Numbers in an Array](https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/)

### Naive Solution (O(n^2) time complexity) (Time Limit Exceeded Error)

```csharp
public int FindMaximumXOR(int[] nums) {
	int max = 0;
	
	for(int i = 0; i < nums.Length; i++){
		for(int j = i+1; j < nums.Length; j++){
			max = Math.Max(max, nums[i] ^ nums[j]);
		}
	}
	
	return max;
}
```

### Using Trie

```csharp
public class Solution {
    public int FindMaximumXOR(int[] nums) {
        int n = nums.Length;
        
        Trie root = new Trie();
        
        foreach(int num in nums){
            Trie tempNode = root;
            string bin = this.NumToBin(num);
            
            foreach(char c in bin){
                int bit = c == '0' ? 0 : 1; 
                
                if(tempNode.children[bit] == null){
                    tempNode.children[bit] = new Trie();
                }
                
                tempNode = tempNode.children[bit];
            }
        }
    
        int maxSoFar = 0;
        
        foreach(int num in nums){
            Trie tempNode = root;
            string bin = this.NumToBin(num);
            int sum = 0;
            int power = 31;
            
            foreach(char c in bin){
                int bit = c == '0' ? 0 : 1;
                int otherBit = c == '0' ? 1 : 0; 
                
                if(tempNode.children[otherBit] != null){
                    sum += (int)Math.Pow(2, power);
                    tempNode = tempNode.children[otherBit];
                }
                else{
                    tempNode = tempNode.children[bit];
                }
                
                power--;
            }     
            
            maxSoFar = Math.Max(maxSoFar, sum);
        }
        
        return maxSoFar;
    }
    
    public string NumToBin(int num){
        string output = Convert.ToString(num, 2);
        output = new string('0', 32-output.Length) + output; 
        return output;
    }
}

public class Trie{
    public Trie[] children;
    
    public Trie(){
        children = new Trie[2];
    }
}
```
