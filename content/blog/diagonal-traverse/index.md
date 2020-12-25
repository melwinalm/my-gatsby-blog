---
title: Diagonal Traverse
date: "2020-12-25"
type: problem-solving
description: Diagonal Traverse
---

Note: This problem was taken from LeetCode - [Diagonal Traverse](https://leetcode.com/problems/diagonal-traverse/)

### Simulation

```csharp
public int[] FindDiagonalOrder(int[][] matrix) {
	int rows = matrix.Length;
	
	if(rows == 0){
		return new int[]{};
	}
	
	int cols = matrix[0].Length;
	
	List<int> output = new List<int>();
	
	int i = 0;
	int j = 0;
	
	int direction = 1;
	
	while(i < rows && j < cols){
		output.Add(matrix[i][j]);
		
		int newRow = i + (direction == 1 ? -1 : 1);
		int newCol = j + (direction == 1 ? 1 : -1);
		
		if(newRow < 0 || newRow == rows || newCol < 0 || newCol == cols){
			if(direction == 1){
				i += (j == cols-1 ? 1 : 0);
				j += (j < cols-1 ? 1 : 0);
			}
			else{
				j += (i == rows-1 ? 1 : 0);
				i += (i < rows-1 ? 1 : 0);
			}
			
			direction = 1-direction;
		}
		else{
			i = newRow;
			j = newCol;
		}
	}
	
	return output.ToArray();
}
```
