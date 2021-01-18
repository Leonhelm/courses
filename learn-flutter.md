# Изучаем Flutter [[udemy](https://www.udemy.com/course/learn_flutter/learn/lecture/16405680)]
* [Листинг примеров из курса](https://github.com/Virer2013/Learn_Flutter)


## Основы
* Суть виджетов: **UI = f(State)**
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
* Практика: [реализация шаблона приложения по погоде](https://github.com/Virer2013/Learn_Flutter/blob/master/layout_interface/lib/main.dart)
* Виджет `ListView` - позволяет создавать [статические](https://github.com/Virer2013/Learn_Flutter/blob/master/static_listview/lib/main.dart) или [динамические](https://github.com/Virer2013/Learn_Flutter/blob/master/dynamic_listview/lib/main.dart) ([динамический с заголовком](https://github.com/Virer2013/Learn_Flutter/blob/master/dynamic_listview_heading/lib/main.dart)) списки (с прокруткой)
* `ListView.builder` - лениво создаёт элементы списка, рендерятся только те, которые есть на экране
* Виджет `Card` - карточка
* Виджет `ListTile` - карточка в списке
* `List.generate` - создание виджетов требуемого количества


## Навигация и передача данных
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
