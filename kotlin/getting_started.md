# WIP Wrap dump of useful info in kotlin

## Useful/used packages:
 - Ktor -> Web Server / API framework
 - Retrofit2 -> HTTP Client, with kinda ORM-like mapping api to objects
 - Jackson -> Serializer/Deserializer
 - KMongo -> Official MongoDB Client

## Cool language features:

### it keyword
Allows implicit variable declaration, usually used in lambdas
```kotlin
fun getIds(list: List<SomeObject>){
  return list.map { it.id }
}
```
The it keyword here takes saves us to avoid typing:
```kotlin
fun getIds(list: List<SomeObject>){
  return list.map { item:SomeObject -> item.id }
}
```
### Collections vs Sequences
source:[collections-and-sequences-in-kotlin](https://medium.com/androiddevelopers/collections-and-sequences-in-kotlin-55db18283aca)
Collections eagerly evaluate your data while sequences do so lazily. Depending on the size of your data, pick the one that fits best: collections — for small lists or sequences — for larger ones, and pay attention to the order of the transformations.

```kotlin
listOf(1,2,3,4)
  .map(it + 1)
  .first( it % 5 == 0)
```

#### Collections
 - map is called —> a new ArrayList is created. We iterate through all items of the initial collection, transform it by copying the original object and changing the color, then add it to the new list.
 - first is called —> we iterate through each item until the first square is found
#### Sequences
 - asSequence —> a sequence is created based on the Iterator of the original collection
 - map is called —> the transformation is added to the list of operations needed to be performed by the sequence but the operation is NOT performed
 - first is called —> this is a terminal operation, so, all the intermediate operations are triggered, on each element of the collection. We iterate through the initial collection applying map and then first on each of them. Since the condition from first is satisfied by the 2nd element, then we no longer apply the map on the rest of the collection.

When working with sequences no intermediate collection is created and since items are evaluated one by one, map is only performed on some of the inputs.
