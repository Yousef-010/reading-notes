# Reading 05 
#### Big O notation
#### Linked List 
 > Hi I toke the fifth idea which is ** write a quiz ** so here is the question based on my reading for that articles >> 

>>> SUB -1-) Big O notation :

- 1_ what is the definition of big O notation?

- 2_The efficiency is evaluated based on 2 factors what are these factors? 

- 3_ we should consider 4 Key Areas for analysis what are these keys? 

- 4_ To quantify the Running Time in our analysis, we will consider Three Measurements of time what are these Measurements? 

- 5_In order to quantify Memory Space, we can consider Four Sources of Memory Usage during function run-time what are these Measurements?  

- 6_ Explain these topics in big O notation: Worst Case, Best Case, Average Case 

> >> The answers : 

- 1 ) notation is used to describe the efficiency of an algorithm or function 

- 2 ) Running Time and Memory Space

- 3 ) Input Size, Units of Measurement, Orders of Growth and Best Case, Worst Case, and Average Case

- 4 ) 
  - The time in milliseconds from the start of a function execution until its end 

  - The number of operations that are executed 

  - The number of “Basic Operations” that are executed

 

- 5 )
  - The amount of space needed to hold the code for the algorithm

  - The amount of space needed to hold the input data

  - The amount of space needed for the output data

  - The amount of space needed to hold working space during the calculation

- 6)

- Worst Case: The efficiency for the worst possible input of size n
   This case runs the longest for all possible inputs of n. This assumes that if we were sorting values, inputs are completely unsorted, and searched values either don’t exist or are at the last to be searched.

- Best Case: The efficiency for the best possible input of size n
   This case runs the quickest for all possible inputs of n. In the case of sorting, this assumes that values are sorted, and so searched- values are easy to find.

- Average Case: The efficiency for a “typical” or “random” input of size n.
   The average case makes a typical assumption about the possible inputs of size ‘n’ and how they might affect efficiency. This is NOT the best case and worst case averaged together.

 

**Review** 

- Big O: The worst-case analysis of algorithm efficiency.
- Running Time: The amount of time required for an algorithm to complete.
- Memory Space: The number of memory resources required for an algorithm to complete.
- Input Size: Represented by the variable n, the total size of values used as parameters in an algorithm.
- Big Omega: The best case analysis of algorithm efficiency.
- Big Theta: The typical or random case used for the analysis of algorithm efficiency.

>>> SUB -2-) Linked List :

- 1 What is a Linked List? 

- 2 what are the types of Linked List? 

- 3 what is Singly - Singly linked list mean? 

- 4 what is Doubly - Doubly linked list mean? 

- 5 what is Node in Nodes linked list mean?

- 6 what is Next in Each linked list mean?

- 7 what is Head in linked list mean?

- 8 what is Current in linked list mean?

---- **MAKE SURE** --- When making your Node class, consider requiring a value to be passed in to require that each node has a value.

>>> Answers : 

- 1 - A Linked List is a sequence of Nodes that are connected/linked to each other. The most defining feature of a Linked List is that each Node references the next Node in the link.

- 2- Singly and Doubly and more 

- 3- Singly - Singly refers to the number of references the node has. A Singly linked list means that there is only one reference, and the reference points to the next node in a linked list.

- 4- Doubly - Doubly refers to there being two (double) references within the node. A Doubly linked list means that there is a reference to both the Next and Previous nodes.

- 5- Node - Nodes are the individual items/links that live in a linked list. Each node contains the data for each link

- 6- Next - Each node contains a property called Next. This property contains the reference to the next node.

- 7- The Head is a reference of type Node to the first node in a linked list.

- 8-Current - The Current is a reference of type Node to the node that is currently being looked at. When traversing, you create a new Current variable at the Head to guarantee you are starting from the beginning of the linked list.

------------------------------------------------------------------------------------------------------------------------------

>> Creation of Linked list: 
```
    class Node:
    
       def __init__(self, dataval=None):
    
          self.dataval = dataval
    
          self.nextval = None
    
     
    
    class SLinkedList:
    
       def __init__(self):
    
          self.headval = None
    
     
    
    list1 = SLinkedList()
    
    list1.headval = Node("Mon")
    
    e2 = Node("Tue")
    
    e3 = Node("Wed")
    
    # Link first Node to second node
    
    list1.headval.nextval = e2
    
     
    
    # Link second Node to third node
    
    e2.nextval = e3
```
 

 >> Traversing a Linked List:
 ```
 
 
    class Node:
    
       def __init__(self, dataval=None):
    
          self.dataval = dataval
    
          self.nextval = None
    
     
    
    class SLinkedList:
    
       def __init__(self):
    
          self.headval = None
    
     
    
       def listprint(self):
    
          printval = self.headval
    
          while printval is not None:
    
             print (printval.dataval)
    
             printval = printval.nextval
    
     
    
    list = SLinkedList()
    
    list.headval = Node("Mon")
    
    e2 = Node("Tue")
    
    e3 = Node("Wed")
    
     
    
    # Link first Node to second node
    
    list.headval.nextval = e2
    
     
    
    # Link second Node to third node
    
    e2.nextval = e3
    
     
    
    list.listprint()
```
 

>> Insertion in a Linked List: 
  - at the Beginning:
```
    class Node:
    
       def __init__(self, dataval=None):
    
          self.dataval = dataval
    
          self.nextval = None
    
     
    
    class SLinkedList:
    
       def __init__(self):
    
          self.headval = None
    
    # Print the linked list
    
       def listprint(self):
    
          printval = self.headval
    
          while printval is not None:
    
             print (printval.dataval)
    
             printval = printval.nextval
    
       def AtBegining(self,newdata):
    
          NewNode = Node(newdata)
    
     
    
    # Update the new nodes next val to existing node
    
       NewNode.nextval = self.headval
    
       self.headval = NewNode
    
     
    
    list = SLinkedList()
    
    list.headval = Node("Mon")
    
    e2 = Node("Tue")
    
    e3 = Node("Wed")
    
     
    
    list.headval.nextval = e2
    
    e2.nextval = e3
    
     
    
    list.AtBegining("Sun")
    
    list.listprint()
```
 

  - at the End :
```
       class Node:
    
       def __init__(self, dataval=None):
    
          self.dataval = dataval
    
          self.nextval = None
    
    class SLinkedList:
    
       def __init__(self):
    
          self.headval = None
    
    # Function to add newnode
    
       def AtEnd(self, newdata):
    
          NewNode = Node(newdata)
    
          if self.headval is None:
    
             self.headval = NewNode
    
             return
    
          laste = self.headval
    
          while(laste.nextval):
    
             laste = laste.nextval
    
          laste.nextval=NewNode
    
    # Print the linked list
    
       def listprint(self):
    
          printval = self.headval
    
          while printval is not None:
    
             print (printval.dataval)
    
             printval = printval.nextval
    
     
    
    list = SLinkedList()
    
    list.headval = Node("Mon")
    
    e2 = Node("Tue")
    
    e3 = Node("Wed")
    
     
    
    list.headval.nextval = e2
    
    e2.nextval = e3
    
     
    
    list.AtEnd("Thu")
    
     
    
    list.listprint()
```
> - ---------------------------T H E E N D ------------------------------------------ 

**_Recourses_** : 

https://www.tutorialspoint.com/python_data_structure/python_linked_lists.htm (Links to an external site.) 