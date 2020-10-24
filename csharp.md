---
date: 2020-10-22T16:13
---

# C#

## Access modifiers


* `public` - the code is accessible for all classes.
* `private` - the code is only accessible within the same class.
* `var` - the complier will determine the type.


## Arrays versus Lists

* In C# __arrays__ and __lists__ are both objects which can be used to hold varaibles. But they are not interchangable.

### Arrays

* Arrays are declared using brackets and contain a reference to the data type which it will hold (string, int).

* For example, an array of integers would look as follows:

```
int [] numbers;
```

* You can then initialise it as follows:

```
int [] numbers = new int[];
```

### Lists

* To create a list you need to call the list and then put the type of list in angled brackets. Then follow that with the name of your list:

```
List<string> Food = new List<string>();
```
* In general it is better to use Lists, as List are more easily sorted, searched, and manipulated.

## What is LINQ?

LINQ or Language Integrated Query is a query syntax in C# to query data from various sources and formats.

Example:

```
// Use LINQ to find teenager students
Student[] teenAgerStudents = studentArray.Where(s => s.age > 12 && s.age < 20).ToArray();
```

### Advantages of LINQ

1. Familiar languge
2. Less coding
3. More readable code
4. Standardize the way of querying multiple data sources


## C# versus Python

* Python is __interpreted__ while C# is __compiled__
* Python is __dynamically__ typed while C# is __statically__ typed. This means that Python figures out your variable type at runtime. For C# all types must be known before runtime. 
* Python and C# are both open-source. 
* C# program files are saved with the `.cs` extension while Python files are saved with the `.py` extension.




