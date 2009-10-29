# Автозагрузка

Kohana использует все преимущества [автозагрузки](http://php.net/manual/language.oop5.autoload.php) в PHP. Это позволяет не использовать функции [include](http://php.net/include) или [require](http://php.net/require) перед использованием класса.

Классы подгружаются с помощью метода [Kohana::auto_load], который использует простое преобразование имени класса в имя файла:

1. Классы располагаются в категории `classes/` в [файловой системе](start.filesystem) фреймворка
2. Все нижние подчёркивания в имени класса заменяются на слеши
2. Имя файла пишется в нижнем регистре

При вызове ещё не подгружённого класса (например, `Session_Cookie`), Kohana будет искать с помощью [Kohana::find_file] файл `classes/session/cookie.php`.

## Пользовательские автозагрузчики

[!!] Системный автозагрузчик инициализируется в `application/bootstrap.php`.

Дополнительные загрузчики классов могут быть добавлены с помощью [spl_autoload_register](http://php.net/spl_autoload_register).