---
title: Evaluate Division
date: "2020-09-27"
type: problem-solving
description: Evaluate Division
tags: csharp
---

Note: This problem was taken from LeetCode - [Evaluate Division](https://leetcode.com/problems/evaluate-division/)

### Depth First Search

```csharp
public double[] CalcEquation(IList<IList<string>> equations, double[] values, IList<IList<string>> queries) {
	
	Dictionary<string, List<string>> graph = new Dictionary<string, List<string>>();
	Dictionary<string, List<double>> graphValues = new Dictionary<string, List<double>>();
	
	for(int i = 0; i < equations.Count; i++){
		string[] equation = equations[i].ToArray();
		
		if(!graph.ContainsKey(equation[0])){
			graph[equation[0]] = new List<string>();
			graphValues[equation[0]] = new List<double>();
		}
		
		if(!graph.ContainsKey(equation[1])){
			graph[equation[1]] = new List<string>();
			graphValues[equation[1]] = new List<double>();
		}
		
		graph[equation[0]].Add(equation[1]);
		graph[equation[1]].Add(equation[0]);
		
		graphValues[equation[0]].Add(values[i]);
		graphValues[equation[1]].Add(1/values[i]);
		
	}
	
	double[] output = new double[queries.Count];
		
	for(int j = 0; j < queries.Count; j++){
		string[] query = queries[j].ToArray();

		output[j] = this.DFS(graph, graphValues, query[0], query[1], new HashSet<string>(), 1.0);

		if(output[j] == 0.0){
			output[j] = -1;
		}
	}
	
	return output;
}
	
public double DFS(Dictionary<string, List<string>> graph, Dictionary<string, List<double>> graphValues, string sNode, string eNode, HashSet<string> visited, double val){

	if(visited.Contains(sNode)){
		return 0.0;
	}

	if(!graph.ContainsKey(sNode)){
		return 0.0;
	}

	if(sNode == eNode){
		return val;
	}

	visited.Add(sNode);

	List<string> nodes = graph[sNode];
	List<double> nodeValues = graphValues[sNode];

	double temp = 0.0;

	for(int i = 0; i < nodes.Count; i++){
		temp = this.DFS(graph, graphValues, nodes[i], eNode, visited, val * nodeValues[i]);

		if(temp != 0.0){
			break;
		}
	}

	visited.Remove(sNode);

	return temp;
}
```
