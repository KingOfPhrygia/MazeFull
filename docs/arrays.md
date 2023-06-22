# Arrays

In Python, there is no built-in data structure called "array". However, the Python standard library provides a module called array that allows you to create arrays of numeric values.

# Creating an Array
To create an array, you need to import the array module and call its array() function, passing in a type code and an iterable containing the initial values of the array. Here's an example:


- python Code
import array
Create an array of integers
numbers = array.array('i', [1, 2, 3, 4, 5])
print(numbers)   Output: array('i', [1, 2, 3, 4, 5])

Create an array of floats
floats = array.array('f', [1.0, 2.0, 3.0, 4.0, 5.0])
print(floats)  Output: array('f', [1.0, 2.0, 3.0, 4.0, 5.0])
The first argument to the array() function is a type code that specifies the data type of the elements in the array. For example, the 'i' type code indicates that the array contains integers, while the 'f' type code indicates that the array contains floats. You can find a list of type codes in the Python documentation.

# Accessing Elements
You can access individual elements of an array using indexing, just like with a list. Here's an example:

- python Code
numbers = array.array('i', [1, 2, 3, 4, 5])
print(numbers[0])  # Output: 1
print(numbers[2])  # Output: 3

# Modifying Elements
You can modify elements of an array using indexing and assignment. Here's an example:

- python Code
numbers = array.array('i', [1, 2, 3, 4, 5])
numbers[0] = 10
numbers[2] = 30
print(numbers)  # Output: array('i', [10, 2, 30, 4, 5])

# Array Methods

The array module provides several methods for manipulating arrays. Here are some of the most commonly used methods:

- append(x): Add an element x to the end of the array.
- extend(iterable): Append the elements from an iterable to the end of the array.
- insert(i, x): Insert an element x at position i.
- remove(x): Remove the first occurrence of element x from the array.
- pop(i): Remove and return the element at position i.
- index(x): Return the index of the first occurrence of element x.
- count(x): Return the number of occurrences of element x.
- reverse(): Reverse the order of the elements in the array.
- sort(): Sort the elements in the array.

# Conclusion
Arrays are a data structure in Python that allow you to store collections of numeric values. They are similar to lists, but are more efficient for numerical computations. The array module provides a simple way to create and manipulate arrays in Python.