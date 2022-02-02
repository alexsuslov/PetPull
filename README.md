# PetPull - станок для производства филамента из ПЭТ бутылок

Во первых это название уже стало именем нарицательным. Первым был все же Моторист, а до него еще кто то.
Первые станки были не для для 3D печати, а для метелок...  

Так что во избежание вселенского бурления - будем использовать название PetPull

На основе разработок 

- Виталия Богачева

_кидайте issue если нужно что то добавить_

![main view](img/main.jpg)

Простое, функциональное устройство для переработки бутылок в филамента.  

- [Обзорное видео тут](https://youtu.be/G16bqoB8Z38)
- [Схема устройства](pdf/2019-11-28V1.2.pdf)
- [Печатная плата для ЛУТ](https://drive.google.com/open?id=1dySD1lTDA4rSZQcVADHj6VBQWqIWLeg4)

## Материалы

- Двигатель - Nema 17
- Контроллер - Arduino Nano V3 
- Драйвер - A49888
- Дисплей - LCD 1602 (HD44780)
- Термистор - 100К от 3D принтера
- Нагреватель - 12V*40ВТ от 3D принтера 
- Блок нагревателя -  E3D Volcano от 3D принтера
- Сопло - 0,8мм диаметром для принтера Anet A6
- Металлический уголок из строительного магазина 
- Подшипники - 625ZZ (опционально)

Маленькие саморезы для сборки составной детали бобины  и большие для крепления станка к основанию. 

## Характеристики 

- Энергопотребление - менее 40Вт*ч
- Скорость производства филамента ~ 10-20 см/мин
- Диаметр прутка - 1,7мм^2
- Заполнение прутка ~ 60-80%
- Рабочая температура ~ 160

## Руководство по самостоятельной сборке

- [Копус станка](assembly.md)
- [Сопло экструдера](extruder.md)
- [Бобина для намотки филамента](spool.md)
- [Контроллер скорости протяжки и температуры](controller.md)

## Температура. 
Вопреки оригинальному видео Виталия - я выяснил что температура 250-260С избыточна для производства филамента. В помещении начинает нещадно вонять, как на промзоне Парнас в Питере. При 160 градусах протяжка проходит ровно точно так же, но пластик почти ничем не пахнет.  Работоспособность станка сохраняется и при снижении температуры до 140С, но диаметр прутка начинает плавать. Видимо это не совсем подходящий режим волочения.  

## Минусы технологии

### Пруток короткий.
Прутки из бутылок получаются относительно короткими - 8-20 метров. Для печати большинства небольших деталей этого достаточно, но все же удобнее когда перед началом печати у Вас хотя бы сотня гарантированных метров пластика на катушке. 
Проблему может решить сварочный аппарат для прутков и я позже его продемонстрирую. В контроллере станка для него все предусмотрено.    
Пруток прямой и жесткий 
Норовит размотаться с катушки. Решить можно либо фиксацией свободного хода катушки, либо свиванием прутка при производстве. Пока не думал над этим. 
### Не пруток, а трубка
Думаю если сообщество подключится к вопросу - сможем обеспечить более плотное прессование ленты в прутке. Тут нужно экспериментировать. 
### Толщина ленты разнится от бутылки к бутылке
А следовательно пруток имеет разное заполнение и нужно как-то нормировать скорость подачи пластика. Пока не думал над этим. но думаю решаемо.
### Медленная скорость печати. 
Похоже особенность всего PET пластика.

## Плюсы технологии

Помимо очевидных, тертых-перетертых хочется отметить еще несколько. 

### Отсутствие страха остаться без филамента. 
Это реально круто, когда тебя не особо беспокоит сколько метров у тебя осталось в катушке. Ты знаешь, что если нужно - через пару часов будет столько сколько нужно. 
 
### Пластик более термостойкий и прочный чем ABS и PLA
Экспериментов еще не ставил, но что подсказывает мне что детали можно будет использовать в широких пределах температур и агрессивных средах. Шестерни и втулки из этого пластика реально очень прочные и износостойкие.

### Печать без головной боли
Вчера нужно было печатать ABSом. Время было дорого и нужно было поскорее завершить распечатку деталей.  Поймал себя на мысли что привыкнув печатать PETом, возвращаться к ABS, было неприятно. Это и горячий стол, и деламинация, и платно в конце концов. 

## Спайка прутка
Одно из главных неудобств при печати пластиком из бутылок - маленькая длина - всего 8-10 метров. Печатать объемные детали не удобно - нужно постоянно контролировать печать и своевременно менять материал. Задача сварки отрезков прутка - успешно решена. Расскажу как. 

### Теория
ПЭТ пластик плавится при температуре выше 260 градусов. При медленном охлаждении - кристаллизуется приобретая белый цвет,  прочность и хрупкость. При быстром охлаждении остается прозрачным и гибким. Для печати подходит второе состояние, следовательно для получения хорошего шва - нужно его быстро охладить. Требуемая скорость охлаждения около 70 градусов в секунду.  

### Блок нагрева
Для нагрева прутка я изготовил блок нагревателя из отрезка алюминиевого радиатора. В нем нужно просверлить сквозное отверстие диаметром 6мм под ТЭН, сквозное отверстие диаметром 4мм для термотрубки и глухое отверстие диаметром 2мм под датчик температуры. Последнее нужно сделать подальше от ТЭНа и поближе к термотрубке. 

После сварки нужно быстро охладить шов. Для этого подойдет алюминиевый или медный радиатор. В нем нужно сделать сквозное отверстие диаметром 4,2-4,5мм. Вдоль отверстия на поверхность делается пропил шириной 2-2,5мм для установки и извлечения прутка. 


Сварка ABS или PLA пластика не отличается от сварки PET прутка за исключением того что для нее нужна температура ниже - 160-200 градусов. 


