---
title: Alert Using Same Key-Card Three or More Times in a One Hour Period
date: "2020-10-04"
type: problem-solving
description: Alert Using Same Key-Card Three or More Times in a One Hour Period
tags: csharp
---

Note: This problem was taken from LeetCode - [Alert Using Same Key-Card Three or More Times in a One Hour Period](https://leetcode.com/problems/alert-using-same-key-card-three-or-more-times-in-a-one-hour-period/)

### Using Sorted Set + Dictionary
```csharp
public IList<string> AlertNames(string[] keyName, string[] keyTime) {
	Dictionary<string, SortedSet<int>> map = new Dictionary<string, SortedSet<int>>();
	
	for(int i = 0; i < keyName.Length; i++){
		if(!map.ContainsKey(keyName[i])){
			map[keyName[i]] = new SortedSet<int>();
		}
		
		map[keyName[i]].Add(this.ConvertTime(keyTime[i]));
	}
	
	HashSet<string> result = new HashSet<string>();
	
	foreach(var item in map){
		List<int> tempList = new List<int>(item.Value.ToList());
		for(int i = 2; i < tempList.Count; i++){
			if(this.IsSameTimeGroup(tempList[i-2], tempList[i-1]) && this.IsSameTimeGroup(tempList[i-2], tempList[i])){
				result.Add(item.Key);
			}
		}
		
	}
	
	List<string> output = result.ToList();
	
	output.Sort();
	return output;
}

public int ConvertTime(string time){
	string[] timeSplit = time.Split(':');
	int min = Convert.ToInt32(timeSplit[0]);
	int sec = Convert.ToInt32(timeSplit[1]);
	
	return min * 60 + sec;
}

public bool IsSameTimeGroup(int time1, int time2){
	if(Math.Abs(time1 - time2) <= 60){
		return true;
	}
	
	return false;
}
```
