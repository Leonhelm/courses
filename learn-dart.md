# Изучаем Dart [[udemy](https://www.udemy.com/course/learndart/learn/lecture/14881652)]

* [Листинг примеров из курса](https://github.com/Virer2013/Dart-2.5)


## Основы
* Входная точка в программу:
```
void main() {
}
```
* Инструкция `print('')` - аналог `console.log('')` в js.
* Объявление переменных
  * `var <имя переменной>` - тип данных определяется из объявленного значения, при пересвоении менять тип данных `нельзя`
  * `dynamic <имя переменной>` - тип данных определяется из объявленного значения, при пересвоении менять тип данных `можно`
  * `<тип данных> <имя переменной>`, типы данных:
    * bool
    * int
    * double
    * String (UTF-16)
    * Runes (UTF-32)
    * Symbol (`Symbol s = #f` - предоставляет символ `f`)
  * `const [тип данных] <имя переменной>` - изменять нельзя, инициализируется в момент компиляции программы
  * `finale [тип данных] <имя переменной>` - изменять нельзя, инициализируется в момент первого обращения к переменной
* `<имя переменной>.runtimeType` - узнать тип данных переменной
* Многострочкая строка:
```
String text = '''
one
two
''';
```
* Интерполяция (добавление в строку значение переменной):
  * `String text = 'Hello, $name';`
  * `String text = 'Hello, ${name.toUpperCase()}';`
  
  
## Коллекции
* List - упорядоченный набор объектов
  * Фиксированный (с жёстко определённым размером)
  * Нефиксированный (может меняться в размерах)
```
var list1 = [1,2,3]; // нефиксированный список
List<int> list2 = [1,2,3]; // нефиксированный список
var list3 = List(5); // фиксированный список
list1.add(4); // добавляем в конец списка значение
list1.remove(4); // удаляем из списка по значению
list1.addAt(0); // удаляем из списка по ключу
list1.first; // возвращает первый элемент списка
list1.last; // возвращает последний элемент списка
list1.isEmpty; // проверка на пустоту списка
list1.length; // возвращает длину списка
list1.reversed; // возвращает список в обратном напралении
list1.clear(); // очищаем список
```
* Set - неупорядоченный набор уникальных объектов
  * Не может содержать дубликаты
  * Доступ к элементам по индексу невозможен
```
var set1 = {1,2,3};
Set<int> set2 = {1,2,3};
var set3 = Set();
// методы и свойства схожи с List
```
* Map - неупорядоченный набор пары ключ-значение
  * Каждый ключ должен быть уникальным
  * Значения могут повторяться
```
var map1 = {"key1": "value1", "key2": "value2"};
Map<int, String> map2 = {1: "value1", 2: "value2"};
var map3 = Map();
map3.containsKey('key'); // true - если содержит ключ 'key'
map3.update('key', (valueCurrent) => 'valueNew'); // меняем по ключу 'key' значение на 'valueNew'
map3.remove('key'); // удаляем по ключу
map3.isEmpty; // как у List
map3.length; // как у List
map3.clear(); // как у List
```


## Функции
* Объявление
```
[возвращаемый тип данных] <имя функции>([тип данных параметра] <параметр>, ...) {
  [тело функции]
}
// или в одну строку:
[возвращаемый тип данных] <имя функции>([тип данных параметра] <параметр>, ...) => [возвращаемое значение функции]
```
* Необязательные параметры
```
void getPerson (String name, [int age]) {
}
```
* Именованные параметры
```
void getPerson ({String name, int age}) {
}
getPerson(name: '', age: 0);
```
* Анонимная функция
```
var func = () {
};
// или var func = () => null;
```


## Объектно-ориентированное программирование
* Конструктор класса
```
class MyClass {
  MyClass() { // конструктор по-умолчанию объявляется именем класса
  }
  
  MyClass.named() { // именованный конструктор, можно создать объект: var myObj = MyClass.named();
  }
  
  MyClass.redirected(): this(); // конструктор redirected вызывает конструктор по-умолчанию
}

class Car {
  var name;
  var color;

  Car(this.car, this.color) // сразу присваиваем параметры конструктора свойствам объекта
}
```
* Инициализатор
```
class Car {
  String name;
  String color;

  // присваиваем параметры конструктора свойствам объекта
  Car({String carName, String carColor}): name = carName, color = carColor {
  }
}
```
* Геттеры, сеттеры
```
class Car {
  double _percent; // совйство или метод с префиксом _ - приватное
  
  set percent(double per) {
    _percent = (per > 100 || per < 0) ? _percent = 0 : _percent = per;
  }
  
  double get percent {
    return _percent;
  }
}
```
* Константные свойства объекта
```
class Car {
  final var weels = 4; // значение константы в классе можно присвоить до конструктора

  Car(this.weels); // или c помощью параметров конструктора
}
```
* Наследование
```
class Vehicle {
  Vehicle.fromColor() {
  }
}

class Car extends Vehicle {
  Car(): super.fromColor() { // единственное возможное место вызова конструктора родительского класса (до инициализации класса)
  }
}
```
* Переопределение наследуемых методов и свойств
```
class Vehicle {
  void start() {
  }
}

class Car extends Vehicle {
  @override // благодаря этой аннотации можно переопределить методы и свойства родительского класса
  void start() {
    super.start(); // вызов метода родительского класса
  }
}

```
* Интерфейсы
```
class Car {
  String name;
}

class Train {
  void move() {
  }
}

// класс Vehicle реализует интерфейсы Car и Train
// необходимо реализовать все свойства и методы имплементированных интерфейсов
class Vehicle implements Car, Train {
}
```
* Миксины
```
class Car {
  String name;
}

mixin Train {
  void move() {
  }
}

// класс Vehicle реализует миксины Car и Train
// классы миксины и миксины не могут содержать конструкторы
class Vehicle with Car, Train {
}
```
* Абстрактные классы
```
abstract class Vehicle {
  String speed;
  void move();
}

// необходимо реализовать все свойства и методы родительского класса
class Car extends Vehicle {
}
```
* [Обобщения (Generics)](https://github.com/Virer2013/Dart-2.5/blob/master/%5B8%5D%20%D0%9E%D0%9E%D0%9F.%20%D0%A3%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C%202/%D0%9E%D0%B1%D0%BE%D0%B1%D1%89%D0%B5%D0%BD%D0%B8%D1%8F%20(Generics)/main.dart)
## Асинхронное программирование
* [Future](https://github.com/Virer2013/Dart-2.5/blob/master/%5B9%5D%20%D0%90%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%BD%D0%BE%D0%B5%20%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5/Future%20API/main.dart)
* [async/await](https://github.com/Virer2013/Dart-2.5/blob/master/%5B9%5D%20%D0%90%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%BD%D0%BE%D0%B5%20%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5/%20async_await/main.dart)
