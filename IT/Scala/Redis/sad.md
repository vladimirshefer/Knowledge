Как сделать собственный урл-сервис?

Класс `etl.rest.RuleRoute`

```scala
  path("ADDRESS") { //наш сервис будет доступен по адресу /ADDRESS
    post { // post метод
      decodeRequest {
        entity(as[String]) { content =>
          val signupService = new SignupService(options)
          val response = signupService.validateAndRespond(content)
          response.errorMessage match {
            case None      => processSuccess(response.toString, "signup request processed")
            case Some(msg) => processFailure(content, response.toString, response.responseCode)
          }
          processSuccess(response.toString, "auth request processed")
        }
      }
    }
  } ~
  path("production") {
    /***********/
  }
} ~
```

Класс `NAMEService` 

```scala
class SignupService(options: SparkOptions) 
extends MetricsDecoratedRestService [SignupRequest, SignupResponse, String]
```