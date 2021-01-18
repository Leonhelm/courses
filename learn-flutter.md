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
  * Выджеты компоновки и управления (`Row`, `Column`, `Center`)
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
* 
* 
* 
