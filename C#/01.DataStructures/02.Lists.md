# Lists

**1. What is a List<T> in .NET, and how does it differ from an array?**

**Answer** :

A List<T> in .NET is a generic collection that allows dynamic resizing. Unlike arrays, which have a fixed size, List<T> can grow or shrink as elements are added or removed. Additionally, List<T> offers methods for inserting, removing, and searching for elements, providing more flexibility compared to arrays.

```Csharp
    // Example : Declaring and initializing a List <T>
    List <int > numbers = new List <int > { 1, 2, 3, 4, 5 };
    numbers.Add(6); // List dynamically resizes to accommodate the new element
```

**2. Popular List methods :** 

| Question | Method / Property | Description | Example |
|---------|------------------|-------------|---------|
| How does the Add() method work in List<T>? | `Add()` | Adds an element to the end of the list; increases capacity automatically if needed | `names.Add("Alice");` |
| How do you insert an element at a specific position in a List<T>? | `Insert()` | Inserts an element at the specified index and shifts elements | `numbers.Insert(2, 3);` |
| How do you remove an element from a List<T> by value? | `Remove()` | Removes the first occurrence of the specified element | `numbers.Remove(3);` |
| How do you remove an element from a List<T> by index? | `RemoveAt()` | Removes the element at the specified index and shifts elements | `names.RemoveAt(1);` |
| How do you check if a List<T> contains a specific element? | `Contains()` | Checks whether the list contains the specified element | `numbers.Contains(3);` |
| How do you find the index of an element in a List<T>? | `IndexOf()` | Returns the index of the first occurrence or `-1` if not found | `names.IndexOf("Bob");` |
| How do you sort a List<T> in ascending order? | `Sort()` | Sorts the list using the default comparer or a custom comparison | `numbers.Sort();` |
| How do you reverse the order of elements in a List<T>? | `Reverse()` | Reverses the list in place (no new list created) | `numbers.Reverse();` |
| How do you find the count of elements in a List<T>? | `Count` | Returns the number of elements currently in the list | `int count = names.Count;` |
| How do you clear all elements from a List<T>? | `Clear()` | Removes all elements and leaves the list empty | `numbers.Clear();` |
| How do you convert an array to a List<T>? | `ToList()` / `List<T>(array)` | Converts an array to a List using LINQ or constructor | `numbersArray.ToList();` |
| How do you convert a List<T> to an array? | `ToArray()` | Creates a new array with the same elements as the list | `numbers.ToArray();` |
| How do you remove all elements that match a condition in a List<T>? | `RemoveAll()` | Removes all elements that satisfy a predicate | `numbers.RemoveAll(n => n % 2 == 0);` |
| How do you find an element in a List<T> based on a condition? | `Find()` | Returns the first element that matches a predicate or default value | `numbers.Find(n => n > 3);` |
| How do you get a sublist from an existing List<T>? | `GetRange()` | Returns a new list containing a range of elements | `numbers.GetRange(1, 3);` |

**3. How do you ensure thread-safe access to a List<T> in a multithreaded environment? :** 

To ensure thread-safe access, you can either use locks (via the lock statement) or use a thread-safe collection like ConcurrentBag<T> from System.Collections.Concurrent instead of List<T>.

```Csharp
    // Example : Thread - safe access to a List <T> using locks
    private static List <int > numbers = new List <int >();
    private static object lockObject = new object ();

    public void AddNumber ( int number )
    {
        lock ( lockObject )
        {
        numbers.Add(number);
        }
    }
```