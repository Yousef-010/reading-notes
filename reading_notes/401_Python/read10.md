# Reading 10 
    > Stacks and Queues 
- What is a Stack 
- A stack is a data structure that consists of Nodes. Each Node references the next Node in the stack, but does not reference its previous. 
- Common terminology for a stack is
  - Push - Nodes or items that are put into the stack are pushed
  - Pop - Nodes or items that are removed from the stack are popped. When you attempt to pop an empty stack an exception will be raised.
  - Top - This is the top of the stack.
  - Peek - When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.
  - IsEmpty - returns true when stack is empty otherwise returns false.
  
> FILO 
- First In Last Out

> LIFO 
- Last In First Out



> Push
- Pushing a Node onto a stack will always be an O -1-operation
```
    ALOGORITHM push(value)
    // INPUT <-- value to add, wrapped in Node internally
    // OUTPUT <-- none
       node = new Node(value)
       node.next <-- Top
       top <-- Node
```

> Pop 
- Popping a Node off a stack is the action of removing a Node from the top

```
    ALGORITHM pop()
    // INPUT <-- No input
    // OUTPUT <-- value of top Node in stack
    // EXCEPTION if stack is empty
    
       Node temp <-- top
       top <-- top.next
       temp.next <-- null
       return temp.value
```

> Peek 
- When conducting a peek, you will only be inspecting the top Node of the stack.
```
    ALGORITHM peek()
    // INPUT <-- none
    // OUTPUT <-- value of top Node in stack
    // EXCEPTION if stack is empty
    
       return top.value
```

> IsEmpty
```
    ALGORITHM isEmpty()
    // INPUT <-- none
    // OUTPUT <-- boolean
    
    return top = NULL
```


> What is a Queue 
- Common terminology for a queue is 
  - Enqueue - Nodes or items that are added to the queue.
  - Dequeue - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
  - Front - This is the front/first Node of the queue.
  - Rear - This is the rear/last Node of the queue.
  - Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
  - IsEmpty - returns true when queue is empty otherwise returns false.


>FIFO 
- First In First Out 
  - This means that the first item in the queue will be the first item out of the queue.
> LILO 
- Last In Last Out
  - This means that the last item in the queue will be the last item out of the queue.


>Enqueue 
- When you add an item to a queue, you use the enqueue action. This is done with an O -1- operation in time because it does not matter how many other items live in the queue (n); 
```
    ALGORITHM enqueue(value)
    // INPUT <-- value to add to queue (will be wrapped in Node internally)
    // OUTPUT <-- none
       node = new Node(value)
       rear.next <-- node
       rear <-- node
```

>Dequeue
- When you remove an item from a queue, you use the dequeue action. This is done with an O -1- operation in time because it doesn’t matter how many other items are in the queue,
```
    ALGORITHM dequeue()
    // INPUT <-- none
    // OUTPUT <-- value of the removed Node
    // EXCEPTION if queue is empty
    
       Node temp <-- front
       front <-- front.next
       temp.next <-- null
    
       return temp.value
```

> Peek 
- When conducting a peek, you will only be inspecting the front Node of the queue.
```
    ALGORITHM peek()
    // INPUT <-- none
    // OUTPUT <-- value of the front Node in Queue
    // EXCEPTION if Queue is empty
    
       return front.value
```

> IsEmpty
```
    ALGORITHM isEmpty()
    // INPUT <-- none
    // OUTPUT <-- boolean
    
    return front = NULL
```

_______________  THE END  ________________________   THANK YOU FOR READING  __________________________
> Resources 
- https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html