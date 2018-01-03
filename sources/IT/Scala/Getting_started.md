##Установка Scala

- Скачайте и установите [Scala](https://www.scala-lang.org/download/all.html). Надежный вариант - `Scala 2.11.4` 
- Устанавливаем в [переменных системы](https://www.java.com/ru/download/help/path.xml) путь к `Scala/bin`
  - `PATH` - `C:\Program Files (x86)\Scala\bin;`

Scala уже установлена, а вы - прекрасны!

## Проверка в консоли

- Запускаем консоль. `Win+R` - `CMD` - `Enter`
- `> scala`
- `scala> var a = 3`
- `scala> a += 1`
- `scala> a`

## Запуск в Intellij IDEA

- `File - Settings- Plugins` 

- В строке поиска набираем `Scala` 

- Используем кнопку `Browse Repositories` внизу

- Устанавливаем плагин `Scala`. [Скриншот](https://image.prntscr.com/image/37BOq0rxRs2So9QTv7fO4A.png)

- Создаем новый проект

- Правой кнопкой по корню в дереве проекта - `Add framework support` - `Scala`

- Создаем в проекте пакет `src / main / scala / apps `

- Создаем в нем Scala-класс Main

```scala
  object Main {
    def main(args: Array[String]): Unit = {
      println("Hello world!")
    }
  }
```

- Можно запускать!

## Что еще почитать

[Быстрый старт со Scala для начинающих и не очень](https://tproger.ru/articles/scala-tutorial-for-beginners/)



