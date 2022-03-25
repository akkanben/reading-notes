# Reading Notes 30 -- Hash Tables

Sources:

- [Code Fellows article](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)
- [ aul Programming YouTube video](https://www.youtube.com/watch?v=MfhjkfocRR0)
- [Hackerearth article](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)
- [Wikipedia](https://en.wikipedia.org/wiki/Hash_table)

## Hash Tables AKA Hash Map

A hash table is a data structure that maps keys to values. A hash function is used to compute the index into an array of locations referred to as buckets. The hashing arlgorithms are not perfect and sometimes collisions can occur when more than one hashed key matches the same bucket location.

Because hash tables use a hashing algorithm, keys will always be unique, this makes them great for situations where uniqueness comes into play. Hash tables are often used for dictionaries, sets, data caches, and database indexing.

Hash maps take advantage of the O(1) read access in arrays by hashing a useful string and turning it into the index used to access the value.

## Collisions

A variety of mathematical techniques can be used to transform a string into an integer. Inevitably there will be a collision in the hash that gets created. One way to deal with this is to store the keys and values in a linked list, this way if a collision happens the colliding key value pair will be appended to the linked list. 

## Buckets

Another thing to consider with the internals of hash tables is the size of the array. The more buckets for hashes to match the less chances for collision but at the expense of disk space. Finding a balance here is the key difficulty in hash map design.

## Internal Methods

- `Add()` For adding new key/value pairs.
- `Find()` Take in a key and use it to find the corresponding bucket and see if the key exists -- if it does return the value.
- `Contains()` Returns a boolean on if the key exists in the hash table.
- `GetHash()` Takes in a string and returns the index of the array where the key and value should be added.
