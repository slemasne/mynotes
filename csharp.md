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
