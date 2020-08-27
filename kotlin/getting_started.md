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
