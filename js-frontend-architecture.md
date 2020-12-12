# JS: Архитектура фронтенда [[hexlet](https://ru.hexlet.io/courses/js-frontend-architecture)]


## Состояние приложения
* Событийная архитектура и DOM без должного внимания порождают запутанный код буквально сразу
* Необходимость базы данных довольно очевидна и понятна для всех, но то же самое не очевидно во фронтенде. DOM позволяет хранить состояние внутри себя и, более того, провоцирует так делать. Главная проблема такого подхода в отсутствии единого источника правды.
* Первый шаг в построении правильной архитектуры состоит в выделении данных которыми манипулирует приложение из DOM в отдельную переменную на уровне приложения. Это позволит отделить работу с данными от их отображения.
* Дополнительные материалы:
  * [Скрипты, модули и библиотеки](https://ru.hexlet.io/courses/js-frontend-architecture/lessons/state/exercise_unit)
  * [Совершенный код: состояние в модулях](https://ru.hexlet.io/blog/posts/sovershennyy-kod-sostoyanie-v-modulyah)


## Комплексное состояние
* Cостояние — это данные нашего приложения в любой момент времени, например, открытые вкладки в редакторе или браузере
* 