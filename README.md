# deploy
Простой скрипт на питоне, который поможет развернуть ваше приложение.
Данная утилита представляет собой обёртку над такой стандартной
утилитой _systemd_ в *nix подобных системах.

## Установка 
`sudo ./install.sh`

# Использование


## Превратить файл в демон
        Например у вас есть проект телеграм бота на python, где главная программа называется bot.py.
    Чтобы превратить ваше приложение в демон, перейдите в папку вашего проекта:

`cd $YOUR_WORK_DIRECTORY`

И наберите простую комманду

`delpoy bot.py`

        Данная комманда автоматом создаст service из вашего приложения, и переместит в нужную директорию,
    сделав его видимым для systemd. Причём рабочей дирректорией демона по умолчанию ставится дирректория
    вашего проекта. Это важно, если в проекте вы использовали относительные пути. Также названием демона
    будет являтся название папки вашего проекта. Данная комманда только создаёт демон, его ещё надо
    запустить, добавить в автозапуск и тд.

## Запустить демон
Для этого опять же в папке проекта просто выполните:

`delpoy start`

        И не нужно указывать никакого названия демона. Программа сама автоматом определит имя папки
    и на основании этого запустит нужный процесс. Это комманда только один раз запустит ваше приложение
    как демон. То есть теперь вы можете отключиться от сервера и приложение все ещё будет работать как
    независимый процесс.

## Добавить в автозапуск
`delpoy enable`

        Теперь при перезагрузке сервера, вместе со всеми программами будет стартовать и ваше приложение.

## Остановить демон
`delpoy stop`

## Убрать из автозапуска демон
`delpoy disable`

## Удалить демон
`delpoy remove`

        Полезно, если вы ошиблись в параметрах при создании демона и не хотите захломлять сервер ненужными
    нерабочими демонами. Данная коммада удаляет service файлы демона и перезагружает systemd,
    а если ваше приложение в это время работало, то ещё и останавливает его.
