# PicoNES LCD эмулятор NES / Dendy на базе pico pi (RP2040) и экрана от смарт часов

## Что это такое

Эмулятор Nintendo NES для портативной игровой системы [Pimoroni PicoSystem](https://shop.pimoroni.com/products/picosystem) RP2040.

Эмулятор поставляется в комплекте с бесплатной домашней игрой [Blade Buster](https://www.rgcd.co.uk/2011/05/blade-buster-nes.html).

Инструкции по прошивке эмулятора на PicoSystem и загрузке игр приведены ниже.

Сохраняйте и воспроизводите несколько игр Nintendo NES на игровом портативном устройстве Pimoroni PicoSystem RP2040. Для выбора игр предусмотрена система меню.

Есть два варианта воспроизведения звука:

- [С помощью встроенного динамика. Низкое качество] (#звук-через-внутренний-динамик)
- [С помощью простого в изготовлении модулятора динамиков, лучшее качество] (#мод-динамика-для-лучшего-звука)

[Смотрите ниже для получения дополнительной информации о звуке](#звук)

(Примечание: Приведенные ниже скриншоты не отражают фактическое качество изображения. Искажение вызвано камерой)

| ||
| ------------- | ------------- |
| ![изображение](assets/gamescreen.jpeg) | ![изображение](assets/menuscreen.jpeg) |


Нажмите на изображение ниже, чтобы посмотреть демонстрационное видео. [Дополнительные видео, включая звук, смотрите ниже](#видео-со-звуком).

[![Video](https://img.youtube.com/vi/4VYKSMvYWc8/0.jpg)](https://www.youtube.com/watch?v=4VYKSMvYWc8)

## Где купить пикосистему

- Великобритания: [https://shop.pimoroni.com/products/picosystem?variant=32369546985555](https://shop.pimoroni.com/products/picosystem?variant=32369546985555)
- ЕС: [https://www.kiwi-electronics.com/en/picosystem-10913?search=picosystem](https://www.kiwi-electronics.com/en/picosystem-10913?search=picosystem)
- США: [https://www.adafruit.com/product/5289](https://www.adafruit.com/product/5289)

## Звук
### Звук через внутренний динамик
Звук через внутренний пьезодинамик работает, но ограничен из-за ограничений этого динамика.

### Модификация динамика для улучшения звука
Качество звука будет намного лучше (но не идеальным и все еще несколько ограниченным) за счет модификации пикосистемы магнитным динамиком мощностью 8 Ом 1 Вт.
Их можно найти [здесь для НАС](https://www.amazon.com/gp/product/B082658QXL/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) и [здесь для Европы](https://www.amazon.nl/gp/product/B0BTYDS6FY/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1)


> Для этого требуется открыть пикосистему и немного припаять. Это простой мод, но я не беру на себя ответственность, если пикосистема повреждена.

Динамик должен быть припаян красным проводом к разъему RX, а черным - к заземлению (контактная площадка со знаком **-**), как показано ниже:

![изображение](assets/batterymod.png)

> Вы можете переключаться между динамиками в игре комбинацией клавиш Y + Down.

### Видео со звуком



| почувствуйте разницу между динамиками | Покажите возможности мода динамиков|
| ------------- | ------------- |
| [![Видео](https://img.youtube.com/vi/BRUByhx4GDo/0.jpg)](https://youtu.be/BRUByhx4GDo) | [![Видео](https://img.youtube.com/vi/cA9mOWZZN6I/0.jpg)](https://youtu.be/cA9mOWZZN6I) |


## Установка программного обеспечения

### перепрошивка эмулятора и загрузка игр в PicoSystem с помощью приложения Windows
Поскольку слот для SD-карты недоступен, создано сопутствующее приложение для Microsoft Windows, которое позволяет пользователю выбирать игры и загружать их в Pico.
[Дополнительная информация здесь](https://github.com/fhoedemakers/PicoSystemInfoNesLoader).

[Приложение для Windows также включено в последнюю версию этого репозитория] (https://github.com/fhoedemakers/PicoSystem_InfoNes/releases).

Приложение также позволяет перепрошивать эмулятор, если он не установлен или доступна более новая версия. Больше нет необходимости в ручной перепрошивке.

![изображение](assets/Screen.png)

### Установка вручную
Если вы не хотите или не можете использовать приложение Windows

#### Ручная перепрошивка эмулятора в PicoSystem

- Загрузите **PicoSystem_InfoNes.uf2** со страницы [релизы](https://github.com/fhoedemakers/PicoSystem_InfoNes/releases/latest).
- Подключите PicoSystem с помощью кабеля USB-C к компьютеру. Убедитесь, что PicoSystem выключена.
- Нажмите и удерживайте кнопку X, затем кнопку включения питания. Отпустите кнопки, и на вашем компьютере появится диск RPI-RP2.
- Перетащите файл UF2 на диск RPI-RP2. Пикосистема перезагрузится и запустит эмулятор.

#### Загрузка одной игры вручную

> Игра должна иметь расширение .nes

Загрузите ПЗУ с одной игрой, переведя устройство в режим загрузки. (Подключитесь к компьютеру, затем удерживайте нажатой клавишу X и включите устройство)
ПЗУ должно быть размещено по адресу **0x10110000** и может быть передано с помощью [picotool](https://github.com/raspberrypi/picotool).

```
picotool загружает rom.nes -t bin -o 0x10110000
```

**Внимание: адрес загрузки был изменен с 0x10080000 на 0x10110000.** Это связано с дополнительным размером встроенной игры, встроенной в исполняемый файл.

#### Загрузка нескольких игр вручную

> Все игры должны иметь расширение .nes и находиться в одном каталоге

Это можно сделать, создав архив tar и загрузив этот архив в PicoSystem. Максимальный размер архива составляет около 15 МБ

``bash
# текущий каталог должен содержать диски .nes
tar cvf games.tar *.nes
picotool загружает игры.tar -t bin -o 0x10110000
```


## Карты кнопок

- Y: отображается на NES Select
- X: отображается на NES Start

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
- X + A: Переключение частоты кадров.
- Y + A: Увеличение громкости
- Y + B: Уменьшение громкости

> Выбор динамика, уровень громкости и настройки яркости будут сохранены, но только при переходе в меню списка игр (X + Y, затем A) или переключении между играми (Y + Влево, Y + Вправо, Y + Вверх). Выключение устройства не сохранит эти настройки.

### Внутриигровое меню со списком игр
- Вверх/ВНИЗ: Прокрутка списка игр
- A: Запуск выбранной игры
- B: Выход из меню

## Состояние батареи
Состояние батареи отображается при активации внутриигрового меню. Когда уровень заряда батареи падает до 10 процентов или ниже, индикатор отображается постоянно.

## Разрешение экрана
Оригинальная развлекательная система Nintendo имеет разрешение 256x240 пикселей. Пикосистема имеет разрешение 240x240 пикселей. Поэтому на пикосистеме первые и последние 8 пикселей каждой горизонтальной линии не видны.

## Титры
InfoNes запрограммирован [Джеем Кумогатой](https://github.com/jay-kumogata/InfoNES) и портирован для вывода DVI на Raspberry PI Pico [Шуичи Такано](https://github.com/shuichitakano/pico-infones). Я использовал порт Шуичи Такано в качестве отправной точки для этого проекта.

Звуковое программирование с помощью [newschooldev](https://github.com/newschooldev) и [Layer812](https://github.com/Layer812)

## Что нужно сделать

- Код должен быть очищен. Использует части [библиотеки PicoSystem](https://github.com/pimoroni/picosystem).
