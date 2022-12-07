# Read-24 Hashtabels

## What is a Hashtable?
1. Hash :algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose
2. Buckets : what is contained in each index of the array of the hashtable.
3. Collisions :is what happens when more than one key gets hashed to the same location of the hashtable.

## Why do we use them?
1. Hold unique values
2. Dictionary
3. Library

### The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value.we can do a lookup in an O(1) time complexity. This is ideal when quick lookups are required.

## Creating a Hash
1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
3. Insert into the array at that index.

## Methods
1. set()
     1. send the key to the hash() method.
     2. Once you determine the index of where it should be placed, go to that index
     3. Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
     4. If something does exist, add the new key/value pair to the data structure within that bucket.
2. get():he get() method takes in a key, gets the Hash, and goes to the index location specified
   
3. has():The has() method will accept a key, and return a bool on if that key exists inside the hashtable.
   
4. keys():The keys() method returns a collection (array) of unique hash keys.
   
5. hash():The hash() method will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.

Example:
<img src="https://www.digitalbithub.com/media/posts/media/mid-square-method.jpg" >