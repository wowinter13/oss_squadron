# RubySquadron Content
## Проблемы:
### 1. Проблема гемов Daru->Distribution
**TAGS: машинное обучение, анализ данных, Ruby-core**

*Проблема грубо: все работает криво или вообще не работает*

Фактическая проблемы гема заключается в том, что единственный способ создать вектор с n различных значений не очень то "ruby way" - ни один из методов создания векторов не дает возможности синтаксически сахарно наполнить значениями наш вектор, тк гем не умеет принимать больше одного аргумента.


```ruby
 rng = Distribution::Normal.rng(mu, sigma)
 Daru::Vector.new(1000.times.map {rng.call})
 ```
 **Use case**: ситуация, где мы хотим создать массив, где каждый элемент будет иметь значение из "случайного нормального распределения".

##### Решения:
1. Локальное решение: добавить в метод ```new_with_size``` внутри гема возможность принимать более одного аргумента и блоки.

   Can make our code simpler this way:

   ```ruby
   rng = Distribution::Normal.rng(mu, sigma)
   Daru::Vector.new_with_size 1000, &rng
   ```

2.   Глобальное решение: попробовать реализовать вышеуказанное в самом Ruby
  ```ruby
  Array.new 100, &rng
  ```

  «This might make it easier to use in general rather than   the specific context of Daru::Vector. It might be a good addition to the distribution gem.»

**Польза**: Воможность узнать немного больше о математике и анализе данных в Ruby, сделать свой первый PR в не самый вебовый гем или же возможность познакомиться с Ruby Trunk.

### 2. Проблема удаления столбцов csv-таблиц с помощью Ruby CSV#delete (работает на один столбец)
 ##### TODO
## Задачи:
### 1. Дополнить Distribution gem новыми видами распределения
  Есть гем Distribution. У него есть куча крутых методов для получения разных видов распределения (нормальное, гамма и др). Но еще больше методов у него нет.

  Это гуд задача для тех, кто хочет потестить метапрограммирование (его очень много в геме) и для тех кто хочет познакомиться с математикой в рубях.

## Теоретические идеи:
- Телеграм бот, который присылает новые коммиты c репозитория гитхаба. Фичи - поддержка других платформ.
  - У Github крутая апишка и можно оказывается пробросить вебхуки для отправки коммитов во всякие телеграмы.
- Телеграм бот, который позволяет узнать все по счету криптовалюты
  - просто бот, которому вводишь адрес бтк-кошеля, а он берет и использует blockchain.info и какой-нибудь btc-info по очереди и возвращает все транзакции.
- Сервис(?) для поиска самого актуального форка над которым ведется разработка
- Фронтенд: сделать загрузочный экран, где выводится золотое сечение
- Помидоро на windows phone (45 минут, 15 минут) (C#, F#) - таймер.
- Хорошая и удобная напоминалка; Создать удобную кастомную напоминалку с количеством раз и промежутками выбора
- API Wrappers для продуктов Blizzard - diablo, overwatch и тд

## Идеи с реальным назначением:
- Гем, который проверяет файлы на их использование в проекте
  - Идея в том чтоб искать файлы употребление(использование) которых в проекте происходит не чаще одного раза. Можно искать конструкции вида def {name} и их повторы; возвращаем название файла. Нужно для очистки устаревших забытых файлов.
  - Потребность - сколько видел проектов и в каждом есть файлы (речь о легаси), которые нигде не используются. Мне не то чтоб лень это дело самому искать, но раз уж snip-snip'ы и bullet'ы за меня n+1 ищут, так пусть за меня и файлы удаляют.
- Твиттер автомессенджер. Или же более сложный бизнес-вариант - унифицированная СММ платформа с помощью которой можно писать пост в веб-приложении, но сообщения будут отправляться во все соц.сети
- Гем интегратор ActiveMerchant + Я.касса + Shopify - полноценное торговое решение
- VK API Wrapper
- Гем - библиотека фильтров регулярных выражений (по структуре представим, что нужно покрыть готовыми регулярками faker)
  - Некоторые регулярные выражения ну очень часто повторяются. Можно сделать гем, который избавит от них и будет выступать предфильтром.
  - Если грубо, то часто спаршенные данные нужно по какому-то принципу вырывать из текста. Можно создать гем, который будет содержать готовые рецепты на все случаи обычной жизни.
- Telnet на iOS и Android - cейчас добавят на айос файлохранилище Finder (iOS 11) и наконец макодрочеры (aka Я) смогут на своих айфонах сохранять логи и всякую всячину.
В том числе и компилируемый код в файликах, а значит будет бум приложений для кодинга. Можно сделать фишулю как минимум уровня (telnet 127.0.0.1:228) и дать возможность с мобилки общаться с серверами.

## Дзен - задачи вечные:
### Документирование Rails
В Rails чудовищное количество методов не покрыто документацией.
Задачу нельзя решить, но можно:
 1. Зайти в исходники рельсы
 2. Ctrl + Shift + F
 3. :nodoc:
 3. Написать документацию на все, что попало в поиск (пример: activerecord/lib/active_record/attribute.rb)

## Помощь сообществу:
Написать туториал по ML в Ruby. Например, решить задачу с kaggle про Титаник параллельно приводя сравнение(разницу) решений на Ruby/Python. Могу скинуть наработки.

## Чего нет на русской википедии:
Я вообще славянофил и не люблю читать английскую википедию; на одной руби конференции рассказывали, что нет статей на русском про эти штуки => полезно:
1. Реалтайм приложения
2. Quantile function
