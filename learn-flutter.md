# Изучаем Flutter [[udemy](https://www.udemy.com/course/learn_flutter/learn/lecture/16405680)]
* [Листинг примеров из курса](https://github.com/Virer2013/Learn_Flutter)


## Основы
* Виджет `MaterialApp`
  * `import 'package:flutter/material.dart'`
  * Корневой виджет для использования темы материала
  * Благодаря параметру `home` позволяет пользоваться хот-релоадом
  * [Гайдлайны по материал дизайну](https://material.io/design)
* Виджет `Scaffold`
  * Отвечает за создание структуры и базового стиля страницы
  * Как правило реализуетсы в параметре `home` виджета `MaterialApp`
* Категории виджетов:
  * Видимые виджиты (`FloatingButton`, `Text`, `Image`)
  * Layout виджеты компоноки и управления (`Row`, `Column`, `Center`)
  * Виджет `Container` - совмещает отображение и компоновку
* Типы виджетов:
  * [Stateless](https://github.com/Virer2013/Learn_Flutter/blob/master/stateless_widget/lib/main.dart)
  * [Stateful](https://github.com/Virer2013/Learn_Flutter/blob/master/stateful_widget/lib/main.dart)
* Работа с изображениями и ассетами:
  * Виджеты `Image` и `Image.asset`
  * Как правило хранятся в корне проекта в папке `assets`
  * Необходимо прописать путь к каждому ресурсу в `pubspec.yaml` в `flutter.assets`
* Работа со шрифтами:
  * Можно прописывать исползуемый шрифт каждому отдельному виджету, например `Text` через  `fontFamaly`
  * Можно прописать шрифт всему приложению через виджет `MaterialApp`, параметр `theme`
  * Как правило хранятся в корне проекта в папке `fonts`
  * Необходимо прописать путь к каждому ресурсу в `pubspec.yaml` в `flutter.fonts`


## Основы компоновки UI
* Виджет `Padding` - служит для создания отступов
* Виджет `Align` - изменение позиции относительно родительского виджета
* Виджет `Center` - центрирование виджета относительно родителя
* Виджет `Container` - позиционирование и стилизация по многим параметрам
* Виджет `Row` - отображает массив переданных виджетов по горизонтали
* Виджет `Column` - отображает массив переданных виджетов по вертикали
* Виджет `Expanded` - позволяет виджету в `Row` или `Column` занять всё оставшееся пространство
  * При помощи параметра `flex` можно менять коофициент гибкости
* Виджет `Stack` - позволяет накладывать виджеты друг на друга
* Виджет `Positioned` - позволяет абсолютно позиционировать виджет относительно родителя `Stack`
* Виджет `Divider` - линия разделитель
* Виджет `Chip` - прямоугольник со скруглёнными краями
* Виджет `SizedBox` - бокс заданного размера
* Практика: [реализация шаблона приложения по погоде](https://github.com/Virer2013/Learn_Flutter/blob/master/layout_interface/lib/main.dart)
* Виджет `ListView` - позволяет создавать [статические](https://github.com/Virer2013/Learn_Flutter/blob/master/static_listview/lib/main.dart) или [динамические](https://github.com/Virer2013/Learn_Flutter/blob/master/dynamic_listview/lib/main.dart) ([динамический с заголовком](https://github.com/Virer2013/Learn_Flutter/blob/master/dynamic_listview_heading/lib/main.dart)) списки (с прокруткой)
* `ListView.builder` - лениво создаёт элементы списка, рендерятся только те, которые есть на экране
* Виджет `Card` - карточка
* Виджет `ListTile` - карточка в списке
* `List.generate` - создание виджетов требуемого количества
* Виджет `FeatureBuilder` - декларативное ожидание завершение фьючерса с подменой виджета при ожидании [пример](https://github.com/Virer2013/Learn_Flutter/blob/master/manual_serialization/lib/main.dart#L39)
* Виджет `CircularProgressIndicator` - спиннер


## Навигация и передача данных
* `Navigator.push()` - переход на следующую страницу
  * Второй аргумент - коллбек, возвращающий виджет желаемой страницы
* `Navigator.pop()` - переход на предыдущую страницу
  * Второй аргумент - фьючер, с возможными данными для передачи в виджет роута
* Маршрутизация по имени:
  * Имена задаются в виджете `MaterialApp` в аргументе `routes`. Можно задать начальный роут при помощи `initialRoute`
  * Переход на маршрут по имени при помощи `Navigator.pushNamed()`. Аргументом `argumants` можно передать данные для виджета, к которому обратились по имени
* Хороший способ передать данные в виджет по маршруту - коллбек `onGenerateRoute` у виджета `MaterialApp`


## Взаимодействие с пользователем
* Виджет `Form` - контейнер для полей формы, предоставляет расширенные возможности по сохранению, сбросу, валидации
  * [Пример использования](https://github.com/Virer2013/Learn_Flutter/tree/master/form_example/lib)
  * Для считывания данных формы необходимо реализовать класс `TextEditingController` и присвоить полученый объект аргументу `controller` у поля
    * Не забыть очистить `.dispose()` объекты от класса `TextEditingController` при `dispose` родительского виджета
  * Для валидации всей формы необходимо реализовать аргумент `key` у формы `GlobalKey<FormState>()`
* Виджет `TextField` - поле ввода
  * `TextFormField` - это `TextField` обёрнутый инструментами интегрированными с формой (например валидация)
  * `keyboardType` - аргумент для задания типа клавиатуры (полная, телефон, почтовый адрес)
  * `inputFormatters` - аргумент для форматирования вводимых данных
  * `maxLines` - аргумент для создания textarea
* Виджет `DropdownButton` - выпадающий список
  * `DropdownButtonFormField` - это `DropdownButton` обёрнутый инструментами интегрированными с формой
* Управление фокусом поля - через класс `FocusNode`
* Виджет `SnackBar` - вывод сообщения внизу экрана поверх всех элементов
* Виджет `AlertDialog` - окно диалога для отображения информации и вывода кнопок
* Виджет `GestureDetector` - виджет для взаимодействия с жестами пользователя


## Пакеты и зависимости
* [pub.dev](https://pub.dev/) - пакетный менеджер для языка `dart`
* Добавляем зависимости в `pubspec.yaml` в раздел `dependecies`, затем скачиваем командой `flutter pub get`
* Также можно подтянуть зависимость с гита или локального файла
* Для работы не напрямую, а через объект можно юзать `as`. Пример: `import 'package:http/http.dart' as http;`


## Работа с сетью
* Для работы с сетью нужно подключить пакет [http](https://pub.dev/packages/http)
* [Ручная сериализация](https://github.com/Virer2013/Learn_Flutter/tree/master/manual_serialization/lib) `JSON` с помощью методов `json.encode()` и `json.decode()` из пакета `dart.convert`
* [Автоматическая сериализация](https://github.com/Virer2013/Learn_Flutter/tree/master/autogen_serialization/lib) - с помощью пакетов (json_serializable)[https://pub.dev/packages/json_serializable] и (build_runner)[https://pub.dev/packages/build_runner]
  * Сервис по генерации моделей на основе json - [json to dart](https://javiercbk.github.io/json_to_dart/)


## [Управление состоянием](https://flutter.dev/docs/development/data-and-backend/state-mgmt/intro)
* **UI = f(State)**
* Empheral state (локальное состояние)
  * [Stateful Widget](https://github.com/Virer2013/Learn_Flutter/blob/master/vanilla_example/lib/main.dart) `setState() (Vanilla)`
* Application State
  * [Inherited Widget](https://github.com/Virer2013/Learn_Flutter/blob/master/inherited_widget_example/lib/main.dart) [Как правильно использовать унаследованный виджет](https://fooobar.com/questions/15394788/flutter-how-to-correctly-use-an-inherited-widget)
  * [Scoped Model](https://github.com/Virer2013/Learn_Flutter/blob/master/scoped_model_example/lib/main.dart)
  * [Provider](https://github.com/Virer2013/Learn_Flutter/blob/master/provider_example/lib/main.dart) ([пакет provider](https://pub.dev/packages/provider))
  * Redux
  * MobX
  * 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
