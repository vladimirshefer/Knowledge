# Как сделать собственный URL-сервис?

### Класс `etl.rest.RuleRoute`

Чтобы зарегистрировать наш серсис, используйте класс RuleRoute.

Добавляем в цепочку:

```scala
path("ADDRESS") { //наш сервис будет доступен по адресу /ADDRESS
  post {
    decodeRequest {
      entity(as[String]) { content =>
        val nAMEService = new NAMEService(options)
        val response = nAMEService.validateAndRespond(content)
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
class NAMEService(options: SparkOptions) 
extends BaseRestService [NAMERequest, NAMEResponse]
```


Методы:

```scala
def parse(input: String): Option[REQUEST]

def respondSuccess(requestAsJson: String, request: NAMERequest)
(implicit value: String = ""): NAMEResponse
def respondFailure(requestAsJson: String, errorCode: Int, errorMessage: String): NAMEResponse
```

Используйте такую реализацию:

```scala
def parse(input: String): Option[NAMERequest] = {
  Try(Serialization.read[NAMERequest](input)) match {
    case Success(value) => Some(value)
    case Failure(t) => {
      error(s"Deserializing error")
      None
    }
  }
}
```

Почему она не реализована по умолчанию? 

- Сериализацию нельзя унифицировать с помощью generics. :(