# TgBot
## Бот
Бот реализован на языке ```Python``` с помощью библиотеки ```aiogram```.
## Функционал
Бот связан с базой данных, которая имеет записи, имеющие вид:
User Id Telegram | Name document | Document content | date
---------------- | ------------- | ---------------- | ----
String           | String        | blob             | date


В 3-ий столбц (Document content) хранят данные файла в формате ***blob***.
Который преобразуется ботом в новый файл и переименовывается в имя записанное в столбце 2 (Name document).

По запросу пользователя бот проверяет, есть ли именно для данного пользователя данные в базе данных, если есть, то бот создаёт репозиторий и копирует туда файлы из БД принадлежание пользователю. После чего пользователь может получить к ним доступ через мессенджер.

Для конкретики приведу диаграмму состояний:

![statechart](\resources\statechart_diagram.png)

## Описание фиксов

### fix 1.1
Добавлена **FSM** (машина состояний), при отправки команды ```/all```.
Бот запоминает состояние после команды ```/all```. При отправки сообщения не содержащего число, бот выходит из состояния. 
Например:

![statechart](\resources\FSM_test.png)