# Сериализация в Scala

Как мы знаем из Java, хорошим тоном является переопределение `toString`. 
В скала метод `toString` обычно сериализует объект в JSON-формат. 
Библиотека `json4s` позволяет сохранять и парсить JSON объекты.

### Класс Serialization

Первое, что вам нужно, это класс `org.json4s.native.Serialization`, и его 2 метода `read` и `write`

Использование: 

```scala
val json = org.json4s.native.Serialization.write[MyClass](obj)
```
```scala
val obj  = org.json4s.native.Serialization.read[MyClass](json)
```



### Formats

- `FieldSerializer[Test]()`
  - `FieldSerializer.ignore("field")`
- `DefaultFormats`

