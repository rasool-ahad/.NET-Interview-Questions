# Arrays

**1. What is an array in .NET, and how is it declared?**

**Answer** :

An array in .NET is a data structure that stores a **fixed-size sequential collection** of elements of
the same type. Arrays in .NET are zero-indexed, and they can be declared using square brackets
[]

```Csharp
    // Example : Declaring and initializing an array

    int [] numbers = new int [5]; // Declaration with a fixed size of 5
    numbers [0] = 10;
    numbers [1] = 20;
    numbers [2] = 30;
    numbers [3] = 40;
    numbers [4] = 50;

    // Alternatively , initialize an array with values
    int [] numbersInitialized = { 10, 20, 30, 40, 50 };
```

**2. What is the difference between one-dimensional and multi-dimensional array in .NET?**

**Answer** :

A one-dimensional array is a simple linear structure where elements are accessed by a single index. 
A multi-dimensional array (such as a 2D or 3D array) requires multiple indices to access elements and represents more complex structures like matrices or grids.

```Csharp
    // Example : Declaring and initializing a two - dimensional array

    int [,] matrix = new int [3, 2] {
        { 1, 2 },
        { 3, 4 },
        { 5, 6 }
    };

    int value = matrix [1, 1]; // Accessing the element in the second row and second column ( value is 4)
```

**3. What are jagged arrays in .NET, and how do they differ from multidimensional arrays??**

**Answer** :

A jagged array in .NET is an array of arrays, where each element can hold a different-sized array.
Unlike multi-dimensional arrays, where each dimension must have the same length, jagged arrays allow for varying lengths for each array within the structure.

```Csharp
    // Example : Declaring and initializing a jagged array

    int [][] jaggedArray = new int [3][];
    jaggedArray [0] = new int [] { 1, 2, 3 };
    jaggedArray [1] = new int [] { 4, 5 };
    jaggedArray [2] = new int [] { 6, 7, 8, 9 };

    int value = jaggedArray [1][1]; // Accessing the second element of the second array ( value is 5)
```
