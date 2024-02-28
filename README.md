# PicoNES LCD эмулятор NES / Dendy на базе pico pi (RP2040) и экрана от смарт часов

## Что это такое

Эмулятор Nintendo NES для портативной игровой системы.

Эмулятор поставляется в комплекте с бесплатной встроеной игрой [Blade Buster](https://www.rgcd.co.uk/2011/05/blade-buster-nes.html).

Инструкции по прошивке эмулятора на Pico Pi и загрузке игр приведены ниже.

Сохраняйте и воспроизводите несколько игр Nintendo NES на игровом портативном устройстве Pimoroni PicoSystem RP2040. Для выбора игр предусмотрена система меню.

Есть два варианта воспроизведения звука:

- (#звук-через-внутренний-динамик)
- (#мод-динамика-для-лучшего-звука)


## Звук
### Звук через внутренний динамик
Звук через внутренний пьезодинамик работает, но ограничен из-за ограничений этого динамика.

### Модификация динамика для улучшения звука
Качество звука будет намного лучше (но не идеальным и все еще несколько ограниченным) за счет модификации пикосистемы магнитным динамиком мощностью 8 Ом 1 Вт.
Их можно найти [здесь для НАС](https://www.amazon.com/gp/product/B082658QXL/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) и [здесь для Европы](https://www.amazon.nl/gp/product/B0BTYDS6FY/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1)


> Вы можете переключаться между динамиками в игре комбинацией клавиш Y + Down.


## Установка программного обеспечения

### перепрошивка эмулятора и загрузка игр в PicoSystem с помощью приложения Windows
Поскольку слот для SD-карты недоступен, создано сопутствующее приложение для Microsoft Windows, которое позволяет пользователю выбирать игры и загружать их в Pico.
[Дополнительная информация здесь](https://github.com/fhoedemakers/PicoSystemInfoNesLoader).

[Приложение для Windows также включено в последнюю версию этого репозитория] (https://github.com/fhoedemakers/PicoSystem_InfoNes/releases).

Приложение также позволяет перепрошивать эмулятор, если он не установлен или доступна более новая версия. Больше нет необходимости в ручной перепрошивке.

![изображение](assets/Screen.png)

## Назначение кнопок

- Y: NES Select
- X: NES Start

### Внутриигровой
- Y + X: Открывает внутриигровое меню. Просматривайте параметры с помощью кнопок ВВЕРХ / ВНИЗ:
- A Вернуться в меню списка игр (выйти), B Возобновить игру (закрыть).
- Переключить кнопку быстрого огня A. Нажмите A для переключения.
- Переключить кнопку быстрого огня B. Нажмите A для переключения.
- Измените яркость. Нажмите ВЛЕВО или ВПРАВО для изменения.
- Y + ВЛЕВО: Предыдущая игра
- Y + ВПРАВО: Следующая игра
- Y + ВВЕРХ: Запуск встроенной бесплатной игры [Blade Buster](https://www.rgcd.co.uk/2011/05/blade-buster-nes.html)
- Y + Вниз: Переключение между динамиками. (Встроено - Добавлено с помощью мода - Оба - Отключены)
- X + A: Отображение FPS.
- Y + A: Увеличение громкости
- Y + B: Уменьшение громкости

> Выбор динамика, уровень громкости и настройки яркости будут сохранены, но только при переходе в меню списка игр (X + Y, затем A) или переключении между играми (Y + Влево, Y + Вправо, Y + Вверх). Выключение устройства не сохранит эти настройки.

### Внутриигровое меню со списком игр
- Вверх/ВНИЗ: Прокрутка списка игр
- A: Запуск выбранной игры
- B: Выход из меню

## Состояние батареи
Состояние батареи отображается при активации внутриигрового меню.

## Разрешение экрана
Оригинальная развлекательная система Nintendo имеет разрешение 256x240 пикселей. Устройство имеет разрешение 284x240 пикселей. Поэтому на устройстве первые и последние 8 пикселей каждой горизонтальной линии не видны.

## Credits
InfoNes запрограммирован [Джеем Кумогатой](https://github.com/jay-kumogata/InfoNES) и портирован для вывода DVI на Raspberry PI Pico [Шуичи Такано](https://github.com/shuichitakano/pico-infones). Я использовал порт Шуичи Такано в качестве отправной точки для этого проекта.
