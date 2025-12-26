# Dictionaries

**1. What is a Dictionary<TKey, TValue> in .NET and how is it different from other collections?**

**Answer** :

A Dictionary<TKey, TValue> is a generic collection that stores key-value pairs. Each key must be unique, and the values can be retrieved by using the corresponding key. Unlike lists, which store items by index, dictionaries use keys for fast lookups

```Csharp
    // Example : Declaring and initializing a Dictionary
    Dictionary <int , string > dictionary = new Dictionary <int , string >();
    dictionary.Add (1, " Alice ");
    dictionary.Add (2, "Bob ");
    // Access value by key
    string name = dictionary [1]; // " Alice "
```

**2. How do you safely retrieve a value from a dictionary without throwing an exception if the key doesn’t exist?**

**Answer** :

The TryGetValue() method allows you to safely retrieve a value from the dictionary. 
It returns true if the key is found, along with the value, or false if the key doesn’t exist.

```Csharp
    // Example : Using TryGetValue to safely retrieve a value
    Dictionary <int , string > dictionary = new Dictionary <int , string >
    {
    { 1, " Alice " },
    { 2, "Bob " }
    };

    if ( dictionary.TryGetValue(1, out string value ))
    {
    Console.WriteLine( value ); // " Alice "
    }
    else
    {
    Console.WriteLine(" Key not found ");
    }
```

**3. How do you iterate through all key-value pairs in a dictionary in .NET ?**

**Answer** :

You can iterate through a dictionary using a foreach loop, where each iteration provides a KeyValuePair<TKey, TValue> that contains both the key and value.

```Csharp
    // Example : Iterating through a Dictionary

    Dictionary < string , int > ageDictionary = new Dictionary < string , int >
    {
        { " Alice ", 25 },
        { "Bob", 30 }
    };
    foreach ( KeyValuePair < string , int > entry in ageDictionary )
    {
        Console.WriteLine($"{ entry . Key } is { entry . Value } years old .");
    }
```


**4. Can you use a custom type as a key in a dictionary in .NET?**

**Answer** :

Yes, you can use a custom type as a key in a dictionary, but the custom type must implement the GetHashCode() and Equals() methods to ensure that keys are compared and hashed correctly

```Csharp
    // Example : Using a custom type as a key in a Dictionary
    class Person
    {
    public string FirstName { get ; set ; }
    public string LastName { get ; set ; }
    public override bool Equals ( object obj )
    {
    return obj is Person person &&
    FirstName == person.FirstName &&
    LastName == person.LastName ;
    }

    public override int GetHashCode ()
    {
    return HashCode.Combine(FirstName, LastName);
    }
    }
    Dictionary <Person , int > personAgeDictionary = new Dictionary < Person , int >();
    personAgeDictionary.Add( new Person { FirstName = " Alice ", LastName = " Smith " });
```

**5. How do you copy a dictionary to another dictionary in .NET?**

**Answer** :

You can copy one dictionary to another by using the Add() method or by initializing the new dictionary with the old dictionary using the constructor.

```Csharp
    // Example : Copying a Dictionary

    Dictionary < string , int > original = new Dictionary < string , int >
    {
    { " Alice ", 25 },
    { "Bob", 30 }
    };

    Dictionary < string , int > copy = new Dictionary < string , int >( original ); // Copies the dictionary
```

**6. How do you work with read-only dictionaries in .NET?**

**Answer** :

You can create a read-only dictionary by wrapping an existing dictionary using the ReadOnlyDictionary<TKey, TValue> class, 
which ensures that no modifications can be made to the dictionary.

```Csharp
    // Example : Creating a read - only dictionary
    Dictionary < string , int > ageDictionary = new Dictionary < string , int >
    {
        { " Alice ", 25 },
        { "Bob", 30 }
    };
    var readOnlyDict = new ReadOnlyDictionary < string , int >( ageDictionary );
    // readOnlyDict .Add (" Charlie ", 35) ; // This line will throw an exception
```

**7. Popular array methods :**

| Question                                                               | Method / Property | Description                                                                                                       | Example                                                                    |
| ---------------------------------------------------------------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| How do you add key-value pairs to a dictionary in .NET?                | `Add()`           | Adds a new key-value pair to the dictionary. Each key must be unique; adding a duplicate key throws an exception. | `ageDictionary.Add("Alice", 25);`                                          |
| How do you check if a key exists in a dictionary in .NET?              | `ContainsKey()`   | Checks whether the specified key exists in the dictionary and returns `true` or `false`.                          | `dictionary.ContainsKey(1);`                                               |
| How do you remove a key-value pair from a dictionary in .NET?          | `Remove()`        | Removes the key-value pair with the specified key if it exists.                                                   | `ageDictionary.Remove("Alice");`                                           |
| How do you retrieve a value from a dictionary using a key in .NET?     | Indexer `[]`      | Retrieves the value associated with the specified key; throws an exception if the key is not found.               | `string value = dictionary[1];`                                            |
| How do you clear all elements from a dictionary in .NET?               | `Clear()`         | Removes all key-value pairs from the dictionary, leaving it empty.                                                | `dictionary.Clear();`                                                      |
| How do you check how many key-value pairs are in a dictionary in .NET? | `Count`           | Returns the total number of key-value pairs in the dictionary.                                                    | `int count = dictionary.Count;`                                            |
| How do you check if a dictionary contains a specific value in .NET?    | `ContainsValue()` | Checks whether a specific value exists in the dictionary.                                                         | `ageDictionary.ContainsValue(30);`                                         |
| How do you prevent duplicate keys when adding to a dictionary in .NET? | `ContainsKey()`   | Checks for the existence of a key before adding a new key-value pair to prevent duplicates.                       | `if (!ageDictionary.ContainsKey("Alice")) ageDictionary.Add("Alice", 30);` |

**7. How do you ensure thread-safe access to a dictionary in a multi-threaded environment?**

**Answer** :

By Using ConcurrentDictionary<TKey, TValue> class from System.Collections.Concurrent, which is designed for thread-safe access in multi-threaded environments.

```Csharp
    // Example : Using ConcurrentDictionary for thread - safe access

    ConcurrentDictionary <string , int > concurrentDict = new ConcurrentDictionary < string, int >();
    concurrentDict.TryAdd(" Alice ", 25);
    concurrentDict.TryUpdate(" Alice ", 30, 25); // Thread - safe update
`
