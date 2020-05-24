---
title: Custom Sort method using IComparable interface
date: "2020-05-24"
type: problem-solving
description: Custom Sort method using IComparable interface
tags: csharp
---

### Problem Statement

Given an array of students. Sort them by their age. If two or more students have the same age then sort them by the alphabetical order of their name.

### Solution

```csharp
public class Program
{
	static void Main(string[] args)
	{
		List<Student> students = new List<Student>();
		students.Add(new Student("LMN", 11));
		students.Add(new Student("XYZ", 12));
		students.Add(new Student("ABC", 12));
		students.Add(new Student("DEF", 13));

		students.Sort();

		foreach(var item in students)
		{
			Console.WriteLine(item.Name + " - " + item.Age.ToString());
		}
		
		// Output will be
		// LMN - 11
		// ABC - 12
		// XYZ - 12
		// DEF - 13

		Console.ReadLine();
	}

	public class Student : IComparable<Student>
	{
		string name;
		int age;

		public string Name { get { return name; } }
		public int Age { get { return age; } }

		public Student(string _name, int _age)
		{
			this.name = _name;
			this.age = _age;
		}

		public int CompareTo(Student other)
		{
			if(this.Age < other.Age)
			{
				return -1;
			}
			else if(this.Age > other.Age)
			{
				return 1;
			}
			else
			{
				return this.Name.CompareTo(other.Name);
			}
		}
	}
}
```
