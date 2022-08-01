# Read: Hash Tables

> What is a Hashtable?
- Meaning
  - Hash Table is a data structure which stores data in an associative manner. 
  - In a hash table, data is stored in an array format, where each data value has its own unique index value.
  - Access of data becomes very fast if we know the index of the desired data.
- Terminology:
  - Hash - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. 
  - In the case of a hashtable, it is used to determine the index of the array.
- Benefits: 
  - The main advantage of hash tables over other data structures is speed . 
  - The access time of an element is on average O(1), therefore lookup could be performed very fast.
  - Hash tables are particularly efficient when the maximum number of entries can be predicted in advance.


> Properties of a Good Hash Function
- Uniformity
  - A good hash function must map the keys as evenly as possible. 
  - This means that the probability of generating every hash value in the output range should roughly be the same. 
  - This also helps in reducing collisions.
- Deterministic
  - A hash function must always generate the same hash value for a given input value.
- Low Cost
  - The cost of executing a hash function must be small so that using the hashing technique becomes preferable over other traditional approaches.


> Types of Hashtable
- Division Method
- Multiplication Method
- Mid-Square Method
- Collisions
- Open Addressing
- Chaining



> what is buket
- Buckets - A bucket is what is contained in each index of the array of the hashtable. 
- Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.


> what is Collisions  
- Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable


> usage
- Hold unique values
- Dictionary
- Library


> Applications of Hash Table
- Hash tables are implemented where
  - constant time lookup and insertion is required
  - cryptographic applications
  - indexing data is required


> image 

![image](https://www.tutorialspoint.com/data_structures_algorithms/images/hash_function.jpg)



> Basic operations on hashtable
- Search − Searches an element in a hash table.
- Insert − inserts an element in a hash table.
- delete − Deletes an element from a hash table.


> Set up the Hashtable
- DataItem
  - Define a data item having some data and key, based on which the search is to be conducted in a hash table.
```
struct DataItem {
int data;
int key;
};
```

- Hash Method
  - Define a hashing method to compute the hash code of the key of the data item.
```
int hashCode(int key){
   return key % SIZE;
}
```


> search operation
- given element is to be searched, compute the hash code of the key passed and locate the element using that hash code as index in the array.
```
struct DataItem *search(int key) {
   //get the hash
   int hashIndex = hashCode(key);
   //move in array until an empty
   while(hashArray[hashIndex] != NULL) {
      if(hashArray[hashIndex]->key == key)
         return hashArray[hashIndex];
      //go to next cell
      ++hashIndex;
      //wrap around the table
      hashIndex %= SIZE;
   }
   return NULL;        
}
```

> Insert Operation
- given an element is to be inserted, compute the hash code of the key passed and locate the index using that hash code as an index in the array.
```
void insert(int key,int data) {
   struct DataItem *item = (struct DataItem*) malloc(sizeof(struct DataItem));
   item->data = data;  
   item->key = key;     
   //get the hash 
   int hashIndex = hashCode(key);
   //move in array until an empty or deleted cell
   while(hashArray[hashIndex] != NULL && hashArray[hashIndex]->key != -1) {
      //go to next cell
      ++hashIndex;
      //wrap around the table
      hashIndex %= SIZE;
   }
   hashArray[hashIndex] = item;        
}
```

> Delete operation
- given an element is to be deleted, compute the hash code of the key passed and locate the index using that hash code as an index in the array.
```
struct DataItem* delete(struct DataItem* item) {
   int key = item->key;
   //get the hash 
   int hashIndex = hashCode(key);
   //move in array until an empty 
   while(hashArray[hashIndex] !=NULL) {
      if(hashArray[hashIndex]->key == key) {
         struct DataItem* temp = hashArray[hashIndex]; 
         //assign a dummy item at deleted position
         hashArray[hashIndex] = dummyItem; 
         return temp;
      } 
      //go to next cell
      ++hashIndex;
      //wrap around the table
      hashIndex %= SIZE;
   }
   return NULL;        
}
```


> Resources
- https://www.thedshandbook.com/hash-tables/
- https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html
- https://www.programiz.com/dsa/hash-table
- https://www.edureka.co/blog/hash-tables-and-hashmaps-in-python/
- https://realpython.com/python-hash-table/
- https://www.youtube.com/watch?v=MfhjkfocRR0&ab_channel=PaulProgramming
- https://en.wikipedia.org/wiki/Hash_table