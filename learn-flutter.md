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
* [Автоматическая сериализация](https://github.com/Virer2013/Learn_Flutter/tree/master/autogen_serialization/lib) - с помощью пакетов [json_serializable](https://pub.dev/packages/json_serializable) и [build_runner](https://pub.dev/packages/build_runner)
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


## Хранение данных на устройстве
* [https://pub.dev/packages/path_provider](path_provider) - независимый от платформы способ доступа к часто используемым расположениям в файловой системе устройства
* [https://api.dart.dev/stable/2.13.4/dart-io/dart-io-library.html](dart-io) - Поддержка файлов, сокетов, HTTP и других операций ввода-вывода для не веб-приложений
* [https://pub.dev/packages/shared_preferences](shared_preferences) - для хранения постоянных небольших данных на диске устройства пользователя (типа localeStorage из js)
* [https://pub.dev/packages/sqflite](sqflite) - для работы с локальной бд SQLite. Особенность: получает и принимает данный исключительно в типе Map


## Bloc
* [Официальна документация](https://bloclibrary.dev/#/ru/gettingstarted)
* Базовая схема:
```
|----|  <- states  |------|  async request ->   |------|
| UI |             | BLoC |                     | Data |
|----|  events ->  |------|  <- async responce  |------|
```
UI - слой представления (Presentation)

BLoC - слой bloc (Business logic)

Data - слой данных (Data layer)

* Устройство BLoC:
```
                                      BLoC
                   |------------------------------------------------|
Stream<Events> -> sink -> Business logic -> StreamController -> stream -> Stream<States>          
                   |------------------------------------------------|
```
StreamController - стандартный класс dart, обёртка над объектом Stream, позволяет организовывать потоки данных

sink - Входящий поток данных, куда пользователь добавляет события

stream - Выходной поток данных, который слушают один или несколько объектов, и реагирует на изменения

* Выше описано поведение поведение блок в чистом виде (без сторонних пакетов). Чаще всего подход блок используют при помощи библиотеки [flutter_bloc](https://pub.dev/packages/flutter_bloc).
* [Хороший пример приложения](https://github.com/Virer2013/Learn_Flutter/tree/master/bloc_network_example) с использованием подхода блок (flutter_bloc) для реализации запросов к апи.
* Кубиты - возможность 6+ версии [flutter_bloc](https://pub.dev/packages/flutter_bloc). Представляют собой блок с меньшим количеством бойлерплейта. Основное отличие в схеме ниже:
```
|----|  <- states     |-------|  async request ->   |------|
| UI |                | Cubit |                     | Data |
|----|  functions ->  |-------|  <- async responce  |------|
```
От `UI` к `Cubit` вместо `events` используются `functions`. [Пример реализации тут](https://github.com/Virer2013/Learn_Flutter/tree/master/cubit_network_example_null_safety/lib/cubit).


## [Чистая архитектура](https://www.udemy.com/course/learn_flutter/learn/lecture/26383244)
#### Независимость от фреймворка
Архитектура не зависит от существования какой-либо библиотеки. Это позволяет использовать Фреймворк в качестве инструмента, вместо того, чтобы втискивать свою систему в рамки его ограничений
#### Независимость от UI
Пользовательский интерфейс можно легко изменить, не изменяя остальную систему. Например, веб-интерфейс может быть заменен на консольный, без изменения бизнес-правил
#### Независимость от базы данных
Вы можете поменять Огасе или SQL Server на MongoDВ, BigTable, CouchDB или что-то еще. Ваши бизнес-правила не связаны с базой данных
#### Независимость от какого-либо внешнего сервиса
По факту ваши бизнес правила просто ничего не знают о внешнем мире
#### Тестируемость
Бизнес-правила могут быть протестированы без пользовательского интерфейса, базы данных, веб-сервера или любого другого внешнего компонента

Развёрнутая схема:
![image](https://user-images.githubusercontent.com/20487810/140644467-a983e557-4e2e-45cd-8a79-5cc9f98acf21.png)

Схема под флаттер:
![image](https://user-images.githubusercontent.com/20487810/140644765-adca6159-5811-4a32-937a-769a3ca646ec.png)

### Dependency Injection

Процесс предоставления внешней зависимости программному компоненту. В полном соответствии с принципом единственной ответственности объект отдаёт заботу о построении требуемых ему зависимостей внешнему, специально предназначенному для этого общему механизму.

Реализуется с помощью инструмента [get_it](https://pub.dev/packages/get_it). Пример [locator_service](https://github.com/Virer2013/Learn_Flutter/blob/master/rick_and_morty/lib/locator_service.dart).

Работа с Service Locator на 2 этапа:

* Регистрация объектов:
  * registerFactoryParam<T, P1,P2>
  * registerFactoryParamAsync<T, P1,P2>
  * registerSingleton<T >
  * registerSingletonAsync<T >
  * registerLazySingleton<T >
  * registerLazySingletonAsync<T >
  * registerSingletonWithDependencies
* Получение объектов:
  * registerFactory<T > get<T>(name, param1, param2)
  * registerFactoryAsync<T > getAsync<T>(name, param1, param2)
