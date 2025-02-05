<p align="center"><img src="https://raw.githubusercontent.com/azamatmurdalov/rage/master/logo.png"></p>

# Превью

Каждый из нас когда-то хотел создать своего голосового помощника.
Так вот я решил создать своего.
Все началось с того, что я прочел комикс Rage of Ultron (отсюда и название).
После прочтения данного комикса я решил, что буду заниматься робототехникой.
К счастью я уже знал язык программирования Python,
поэтому не составило особого труда написать программную часть.

На данный момент для воспроизведения голоса робота я использую технологию Yandex SpeechKit Cloud.
В дальнейшем планирую перейти на что-то автономное.


# Функционал

#### Программное обеспечение:

Rage написан на языке программирования Python версии 3.8.5 в стиле ООП.
Он может вести диалог.

Алгоритм работы:
Сначала он записыват речь в wav-файл, переводит в текст,
сравнивает его с вопросами из своей базы данных и если находит похожий вопрос,
то берет ответ из базы данных, переводит в речь и озвучивает,
а если не находит вопрос, то он просто говорит: "Я тебя не понимаю".
Вопросы и ответы хранятся в базе данных SQLite3.
Для перевода текста в речь используется технология Yandex SpeechKit CLoud.
Для перевода речи в текст используется библиотека Vosk.
Также используются библиотеки Wave для создания wav-файла и Pygame для воспроизведения wav-файла.

Если задать роботу вопрос "хочешь научиться?", то он предлагает при команде "один" озвучить вопрос,
затем, после команды "два", озвучить ответ, после чего он переводит эти данные в текст и сам записывает в базу данных.
Таким образом робот в каком-то смысле может обучаться.

Если робот отвечает на какой-то вопрос впервые, то он создает новый wav-файл в папке records,
чтоб в следующий раз сразу же воспроизвести этот файл, чем тратить время на синтез речи.
Это делается для более быстрого ответа.

#### Железо:

Тело робота состоит из алюминевой головы с вырезами для глаз и отверстиями для динамиков. Внутри головы находятся микроконтроллер Arduino Uno, два красных диода и музыкальные колонки.
Arduino используется для подсветки диодов, а музыкальные колонки (динамики) используются для воспроизведения речи робота, и они подключены к ноутбуку через провода.
Также у робота есть туловище, но оно пока что не соединено с роботом. Да и робот пока что не может самостоятельно работать и приходится подключать его к ноутбуку.


## Установка

Прежде, чем запустить робота, Вам необходимо создать алиас:

    $ alias rage="chmod +x run.sh && ./run.sh"

## Запуск

    $ rage

# Версии

#### Версия 1.0:

Робот может вести диалог с человеком. Он записыват речь в wav-файл, переводит в текст, сравнивает его с вопросами из своей базы данных и если находит похожий вопрос, то берет ответ из базы данных, переводит в речь и озвучивает, а если не находит вопрос, то он просто говорит: "Я тебя не понимаю". Вопросы и ответы хранятся в базе данных SQLite3.
Для перевода текста в речь и обратно используется технология Yandex SpeechKit CLoud. Также используются библиотеки Wave для создания wav-файла и Pygame для воспроизведения wav-файла.

Тело робота состоит из алюминевой головы с вырезами для глаз и отверстиями для динамиков. Внутри головы находятся микроконтроллер Arduino Uno, два красных диода и музыкальные колонки.
Arduino используется для подсветки диодов, а музыкальные колонки (динамики) используются для воспроизведения речи робота и они подключены к ноутбуку через провода.
Также у робота есть туловище, но оно пока что не соединено с роботом. Да и робот пока что не может самостоятельно работать и приходится подключать его к ноутбуку.

#### Версия 1.1:

Автоматизировано добавление данных в базу данных. Если задать роботу вопрос "хочешь научиться?", то он предлагает при команде "один" озвучить вопрос, затем, после команды "два", озвучить ответ, после чего он переводит эти данные в текст и сам записывает в базу данных. Таким образом робот в каком-то смысле может обучаться.

Если робот отвечает на какой-то вопрос впервые, то он создает новый wav-файл в папке records, чтоб в следующий раз сразу же воспроизвести этот файл, чем тратить время на синтез речи. Это делается для более быстрого ответа от робота.

#### Версия 1.2:

Выполнен переход на Python 3.8.5.
Код переписан с процедурного стиля на ООП.
Добавлена таблица Фразы. Теперь робот произносит различные фразы, если с ним никто не беседует.
Исправлены некоторые баги, связанные с записью команд в базу данных.
