# Stack
A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle, meaning that the last element added to the stack is the first one to be removed. It operates like a physical stack of objects, where items are added and removed from the top.

In a stack, you can only access the top element, and any new elements added to the stack are added to the top. When you remove an element from the stack, it is always the top element that is removed.

Here are some key operations that can be performed on a stack:

- Push: Add an element to the top of the stack.
- Pop: Remove the top element from the stack.
- Peek: Get the value of the top element without removing it from the stack.
- IsEmpty: Check if the stack is empty.
- Size: Get the number of elements in the stack.

Stacks are commonly used in programming for tasks such as maintaining a history of function calls, implementing undo/redo functionality, evaluating mathematical expressions, and more.

# Creating a Stack
In Python, you can create a stack using a list. Here's an example:

- python code
stack = []

# Pushing Elements to the Stack
To add an element to the top of the stack, you can use the append() method on the list. Here's an example:

- python code
stack.append(1)
stack.append(2)
stack.append(3)
Now the stack contains the elements 3, 2, and 1, with 3 at the top.

# Popping Elements from the Stack
To remove the top element from the stack, you can use the pop() method on the list. Here's an example:

- python code
top_element = stack.pop()
print(top_element)  # Output: 3
Now the stack contains the elements 2 and 1, with 2 at the top.

# Peeking at the Top Element
To get the value of the top element without removing it from the stack, you can use the indexing operator on the list. Here's an example:

- python code
top_element = stack[-1]
print(top_element)  # Output: 2

# Checking if the Stack is Empty
To check if the stack is empty, you can use the len() function on the list. Here's an example:

- python code
if len(stack) == 0:
    print("Stack is empty")
else:
    print("Stack is not empty")
Getting the Size of the Stack
To get the number of elements in the stack, you can use the len() function on the list. Here's an example:

- python code
stack_size = len(stack)
print(stack_size)  # Output: 2

# Conclusion
Stacks are a simple but powerful data structure in Python that allow you to add and remove elements in a specific order. They are commonly used in programming for a wide range of tasks, and can be implemented using a list in Python. Understanding how to use stacks can help you write more efficient and elegant code.