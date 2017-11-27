# Как сделать собственный урл-сервис?

### Класс `etl.rest.RuleRoute`

Чтобы зарегистрировать серсис, используйте класс RuleRoute.

Добавляем 

```scala
path("ADDRESS") { //наш сервис будет доступен по адресу /ADDRESS
```

Copy+Paste:

```scala
    post {
      decodeRequest {
        entity(as[String]) { content =>
```

```scala
          val nAMEService = new NAMEService(options)
          val response = nAMEService.validateAndRespond(content)
```

Copy+Paste

```scala
          response.errorMessage match {
            case None      => processSuccess(response.toString, "signup request processed")
            case Some(msg) => processFailure(content, response.toString, response.responseCode)
          }
          processSuccess(response.toString, "auth request processed")
        }
      }
    }
  } ~
```



### Класс `NAMEService`

```scala
class SignupService(options: SparkOptions) 
extends MetricsDecoratedRestService [SignupRequest, SignupResponse, String]
```



У класса `MetricsDecoratedRestService` есть 4 метода

1. `def validate (input: NAMERequest): Boolean`

2. `def respondSuccess (inputAsJson: String, input: NAMERequest): NAMEResponse`

3. `def respondFailure (inputAsJson: String, input: NAMERequest): NAMEResponse`

4.  `def validateAndRespond (inputAsJson: String): Unit`

   ```scala
   def validateAndRespond (input: String): Unit = {
     val request = JsonParseService.toNAMERequest(input)
     if (validate(request)){
       responseSuccess(input, request)
     } else {
       responseSuccess(input, request)
     }
   }
   ```

   ​