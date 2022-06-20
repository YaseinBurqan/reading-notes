# Stacks and Queues

### What is a stack?

Stack: a simple concept that you can think of it as a stack of books in other words last in first out, the way we do this is with a method called push and also pop.

    - data structure consisting of nodes
    - nodes reference next node in stack
    - nodes don’t reference previous node in stack

## Stacks follow these concepts

### FILO

- First In Last Out

    This means that the first item added in the stack will be the last item popped out of the stack.

### LIFO

- Last In First Out

    This means that the last item added to the stack will be the first item popped out of the stack.

<br/>

## Stack Visualization

    the topmost item is denoted as the `top`. When you push something to the stack, it becomes the new `top`. When you pop something from the stack, you pop the current `top` and set the next `top` as `top.next`.

### Common terminology for a stack is

1- Push - put `Nodes` or `items` into the stack .

    ALGORITHM push(value)
    // INPUT <-- value to add, wrapped in Node internally
    // OUTPUT <-- none
    node = new Node(value)
    node.next <-- Top
    top <-- Node

2- Pop - remove `Nodes` from the stack.

    ALGORITHM pop()
    // INPUT <-- No input
    // OUTPUT <-- value of top Node in stack
    // EXCEPTION if stack is empty
    Node temp <-- top
    top <-- top.next
    temp.next <-- null
    return temp.value

3- Top - This is the top of the stack.

4- Peek - view the value of the top Node in the stack after peek.

    ALGORITHM peek()
    // INPUT <-- none
    // OUTPUT <-- value of top Node in stack
    // EXCEPTION if stack is empty
    return top.value

5- IsEmpty - returns true when stack is empty otherwise returns false.

    ALGORITHM isEmpty()
    // INPUT <-- none
    // OUTPUT <-- boolean
    return top = NULL

#

### What is a Queue

## Queues follow these concepts

### FIFO

- First In First Out

    This means that the first item in the queue will be the first item out of the queue.

### LILO

- Last In Last Out

    This means that the last item in the queue will be the last item out of the queue.

<br/>

#### Common terminology for a queue is

1- Enqueue - Nodes or items that are added to the queue.

    ALGORITHM enqueue(value)
    // INPUT <-- value to add to queue (will be wrapped in Node internally)
    // OUTPUT <-- none
    node = new Node(value)
    rear.next <-- node
    rear <-- node

2- Dequeue - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.

    ALGORITHM dequeue()
    // INPUT <-- none
    // OUTPUT <-- value of the removed Node
    // EXCEPTION if queue is empty
    Node temp <-- front
    front <-- front.next
    temp.next <-- null
    return temp.value

3- Front - This is the front/first Node of the queue.

4- Rear - This is the rear/last Node of the queue.

5- Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.

    ALGORITHM peek()
    // INPUT <-- none
    // OUTPUT <-- value of the front Node in Queue
    // EXCEPTION if Queue is empty
    return front.value

6- IsEmpty - returns true when queue is empty otherwise returns false.

    ALGORITHM isEmpty()
    // INPUT <-- none
    // OUTPUT <-- boolean
    return front = NULL

#

resources :
[Stacks and Queues](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)
