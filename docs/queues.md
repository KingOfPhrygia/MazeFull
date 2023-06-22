# Queue
A queue is a linear data structure that follows the First-In-First-Out (FIFO) principle, meaning that the first element added to the queue is the first one to be removed. It operates like a physical queue of people waiting in line, where the first person in line is the first one to be served and leave the line.

In a queue, you can only access the front and rear elements. Any new elements added to the queue are added to the rear, and when you remove an element from the queue, it is always the front element that is removed.

Here are some key operations that can be performed on a queue:

- Enqueue: Add an element to the rear of the queue.
- Dequeue: Remove the front element from the queue.
- Peek: Get the value of the front element without removing it from the queue.
- IsEmpty: Check if the queue is empty.
- Size: Get the number of elements in the queue.
- Queues are commonly used in programming for tasks such as processing tasks in the order they were received, implementing message queues, and more.

#Creating a Queue
In Python, you can create a queue using a list. Here's an example:

- python code
queue = []

# Enqueuing Elements to the Queue
To add an element to the rear of the queue, you can use the append() method on the list. Here's an example:

- python code
queue.append(1)
queue.append(2)
queue.append(3)
Now the queue contains the elements 1, 2, and 3, with 1 at the front and 3 at the rear.

# Dequeuing Elements from the Queue
To remove the front element from the queue, you can use the pop(0) method on the list. Here's an example:

- python code
front_element = queue.pop(0)
print(front_element)  # Output: 1
Now the queue contains the elements 2 and 3, with 2 at the front and 3 at the rear.

# Peeking at the Front Element
To get the value of the front element without removing it from the queue, you can use indexing operator on the list. Here's an example:

- python code
front_element = queue[0]
print(front_element)  # Output: 2
# Checking if the Queue is Empty
To check if the queue is empty, you can use the len() function on the list. Here's an example:

- python code
if len(queue) == 0:
    print("Queue is empty")
else:
    print("Queue is not empty")
    
# Getting the Size of the Queue
To get the number of elements in the queue, you can use the len() function on the list. Here's an example:

- python code
queue_size = len(queue)
print(queue_size)  # Output: 2

# Conclusion
Queues are a simple but powerful data structure in Python that allow you to add and remove elements in a specific order. They are commonly used in programming for a wide range of tasks, and can be implemented using a list in Python. Understanding how to use queues can help you write more efficient and elegant code.