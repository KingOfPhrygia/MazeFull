# linked list

A linked list is a linear data structure in which each element, called a node, is linked to the next node using a pointer. The first node is called the head of the linked list, while the last node is called the tail. Here's an example of a simple linked list:


- Python code
Head -> Node1 -> Node2 -> Node3 -> Tail
Each node in a linked list consists of two parts: the data part and the next part. The data part contains the value of the node, while the next part contains a reference to the next node in the list. If the next part of a node is None, it means that it is the last node in the list.

# Creating a Linked List
To create a linked list, you need to define a Node class that has two properties: data and next. Here's an example:


- Python code
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
The data property stores the value of the node, while the next property stores a reference to the next node in the list. The __init__() method initializes these properties to their default values.

Once you have defined the Node class, you can create a linked list by creating the first node and setting the head of the list to that node. Here's an example:


- Python code
Create the first node
head = Node(1)

Set the head of the list to the first node
linked_list = head

# Adding Nodes
To add a node to the end of a linked list, you need to traverse the list until you reach the tail, and then add the new node after the tail. Here's an example:


- Python code
Traverse the list to find the tail
current = linked_list
while current.next is not None:
    current = current.next

Add the new node after the tail
new_node = Node(2)
current.next = new_node
To add a node to the beginning of a linked list, you simply set the next property of the new node to the current head of the list, and then set the head of the list to the new node. Here's an example:


- Python code
Add a node to the beginning of the list
new_node = Node(0)
new_node.next = linked_list
linked_list = new_node

# Removing Nodes
To remove a node from a linked list, you need to find the node that precedes it, and then update the next property of that node to skip over the node to be removed. Here's an example:


- Python code
Remove the second node from the list
current = linked_list
previous = None
while current is not None and current.data != 2:
    previous = current
    current = current.next
if current is not None:
    previous.next = current.next

# Traversing a Linked List
To traverse a linked list, you start at the head of the list and follow the next property of each node until you reach the tail. Here's an example:


- Python code 
Traverse the list and print each node's data
current = linked_list
while current is not None:
    print(current.data)
    current = current.next

# Conclusion
Linked lists are a powerful and flexible data structure in Python that allow you to store collections of elements in a specific order. They provide a simple way to add, remove, and traverse nodes in the list, making them a popular choice for many programming tasks.