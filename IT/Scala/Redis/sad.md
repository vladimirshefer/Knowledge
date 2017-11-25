# Как сделать собственный урл-сервис?

### Класс `etl.rest.RuleRoute`

Чтобы зарегистрировать наш серсис, используйте класс RuleRoute.

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