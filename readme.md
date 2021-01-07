## Calling 3rd Party Rest Service with Ktor

1. Installing the feature.   
   Apache is the chosen engine and here we use GSON to deserialize response to object

```kotlin
val client = HttpClient(Apache) {  
  install(JsonFeature) {  
  serializer = GsonSerializer()  
    }  
}
```
2. Consume the service
```kotlin
get("consumeservice") {  
  log.info("Consume BEGIN")  
    val result = client.get<SpaceShip>("http://localhost:8080/spaceship")  
    log.info("the result: ${result}")  
    call.respond(result)  
    log.info("Consume END")  
}
```

