# Задание 2*. @CsvFileSource (необязательная задача повышенной сложности)

Мы с вами на лекции разобрали аннотацию `@CsvSource`, внутри которой можно писать строки в формате CSV.

Писать значения прямо в аннотации не плохо, но если их будет штук 50, то, наверное, ничего хорошего из этого не выйдет.

Поэтому хорошо бы воспользоваться возможностями JUnit и аннотации `@CsvFileSource`.

Вам необходимо взять проект с калькулятором бонусов и переписать сценарии таким образом, чтобы данные читались из файла формата CSV.

Сам файл необходимо положить в каталог `resources`, который тоже нужно создать, следующим образом:

![image](https://user-images.githubusercontent.com/53707586/149668473-da63281c-4243-4071-a6cf-89e45036b9d1.png)

Быстро это сделать можно вот так: `Alt + Insert` на каталоге `test` выбираете `New File` и дальше вводите имя файла вместе с именем каталога:

![image](https://user-images.githubusercontent.com/53707586/149668489-54c14f68-9c83-4290-b700-5d2b5def114f.png)

IDEA сама за вас создаст и каталог, и файл.

После чего в боковой панельке следует сделать reimport Maven-проекта:

![image](https://user-images.githubusercontent.com/53707586/149668495-8ceb5cd7-eee0-41d5-96ac-e2b555f9d206.png)

И IDEA поставит вам красивую иконочку на ресурсы для тестов:

![image](https://user-images.githubusercontent.com/53707586/149668513-62555f95-f0f2-440f-927c-4feb0e337f42.png)

Сам файл вы можете редактировать прямо в IDEA, это обычный текстовый файл, но подчиняющийся правилам CSV.

При этом обратите внимание, что кодировка файла UTF8:

![image](https://user-images.githubusercontent.com/53707586/149668544-fd8fc7a2-dd46-4811-800e-51094f0d04d8.png)

Если это не так, кликните на указанном поле и выберите UTF8:

![image](https://user-images.githubusercontent.com/53707586/149668575-749f377d-ec5b-4a06-a3ae-51a19dacd0bc.png)

Например, на лекции было (`value` требовал массив):
```java
  @CsvSource(
      value={
          "'registered user, bonus under limit',100060,true,30",
          "'registered user, bonus over limit',100000060,true,500"
      }
  )
```

Если элемент в массиве только один, то полная запись:
```java
  @CsvSource(
      value={
          "'registered user, bonus under limit',100060,true,30"
      }
  )
```

Сокращённая — работает только с одним элементом:
```java
  @CsvSource(value="'registered user, bonus under limit',100060,true,30")
```

А если вы везунчик, и элемент ещё и называется `value`, то:
```java
  @CsvSource("'registered user, bonus under limit',100060,true,30")
```

Использованная аннотация должна выглядеть следующим образом:
```java
  @CsvFileSource(resources = "/data.csv")
```
