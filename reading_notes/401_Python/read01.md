# Reading 01
## That price is pain, the pain of growth.
### Suffering is dependent on the story that we layer on top of our pain

```html
> ## Things I want to know more about

- what is the uses of Big O notation ?? 
- how we can involve it iside our caode ?? 
- what is the diff between rebinding and mutating in lists 
- how this ` x+=y ` equal this ` x = x.__iadd__(y) ` ?

```

> Big O Notation 
- Big O notation is used in Computer Science to describe the performance or complexity of an algorithm. Big O specifically describes the worst-case scenario
- O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.
```
bool IsFirstElementNull(IList<String> elements)
{
    return elements[0] == null;
}
```

- O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.

```
bool ContainsValue(IEnumerable<string> elements, string value)
{
    foreach (var element in elements)
    {
        if (element == value) return true; 
    }     
    return false; 
}
```
- O(N²) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. 

```
bool ContainsDuplicates(IList<string> elements)
{
    for (var outer = 0; outer < elements.Count; outer++) 
    {
        for (var inner = 0; inner < elements.Count; inner++) 
        { 
            // Don't compare with self 
            if (outer == inner) continue;             
            
            if (elements[outer] == elements[inner]) return true; 
        }
    }    
    return false;
}
```

- O(2^N) denotes an algorithm whose growth doubles with each addition to the input data set. The growth curve of an O(2^N) function is exponential — starting off very shallow, then rising meteorically. 

```
int Fibonacci(int number)
{
    if (number <= 1) return number;
       
    return Fibonacci(number - 2) + Fibonacci(number - 1); 
}
```

> **_we wil take_**
>> [see the link](https://pymotw.com/3/index.html)
- Text  
- Data Structures
- Algorithms
- Dates and Times
- Mathematics
- The File System
- Data Persistence and Exchange
- Data Compression and Archiving
- Cryptography
- Concurrency with Processes, Threads, and Coroutines
- Networking
- The Internet
- Email 
- Application Building Blocks
- Internationalization and Localization
- Developer Tools
- Runtime Features
- Language Tools
- Modules and Packages
- Unix-specific Services
- Porting Notes
- About Python Module of the Week
 
 














