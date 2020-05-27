---
title: Possible Bipartition
date: "2020-05-27"
type: problem-solving
description: Possible Bipartition
tags: csharp
---

Note: This problem was taken from LeetCode - [Possible Bipartition](https://leetcode.com/problems/possible-bipartition/)

### Breadth First Search

```csharp
    public bool PossibleBipartition(int N, int[][] dislikes) {
        List<List<int>> map = new List<List<int>>();
        
        for(int i = 0; i <= N; i++){
            map.Add(new List<int>());
        }
        
        foreach(int[] edge in dislikes){
            map[edge[0]].Add(edge[1]);
            map[edge[1]].Add(edge[0]);
        }
        
        int[] color = new int[N+1];
        
        for(int i = 1; i <= N; i++){
            if(color[i] == 0){
                color[i] = 1;
                Queue<int> bfsQueue = new Queue<int>();
                bfsQueue.Enqueue(i);
                
                while(bfsQueue.Count > 0){
                    int index = bfsQueue.Dequeue();
                    
                    foreach(int j in map[index]){
                        if(color[j] == 0){
                            color[j] = color[index] == 1 ? 2 : 1;
                            bfsQueue.Enqueue(j);
                        }
                        else{
                            if(color[j] == color[index]){
                                return false;
                            }
                        }
                    }
                }   
            }
        }
        
        return true;
    }
```

### Breadth First Search

```csharp
public bool PossibleBipartition(int N, int[][] dislikes) {
	List<List<int>> map = new List<List<int>>();
	
	for(int i = 0; i <= N; i++){
		map.Add(new List<int>());
	}
	
	foreach(int[] edge in dislikes){
		map[edge[0]].Add(edge[1]);
		map[edge[1]].Add(edge[0]);
	}
	
	int[] color = new int[N+1];
	
	for(int i = 1; i <= N; i++){
		if(this.DFS(map, i, color) == false){
			return false;
		}
	}
	
	return true;
}

public bool DFS(List<List<int>> map, int index, int[] color){
	foreach(int j in map[index]){
		if(color[j] == 0){
			color[j] = color[index] == 1 ? 2 : 1;
			if(this.DFS(map, j, color) == false){
				return false;
			}
		}
		else{
			if(color[j] == color[index]){
				return false;
			}
		}
	}
	return true;
}
```
