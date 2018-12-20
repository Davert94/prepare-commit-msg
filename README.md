# prepare-commit-msg

## Описание

Хук гита для автоматизации добавления номера задачи заданного формата в коммит.
(полезно, когда ветки выглядят в духе _feature/<номер задачи>_)

## Принцип работы

Скрипт сначала получает имя ветки. Затем обрезает все до последнего '/' включительно.
Далее идет проверка, что полученное значение ветки числовое. Если нет, то скрипт завершает работу.
Иначе формируем вставку номера задачи заданного формата.

Дальше определяем:
1. Не является ли наша ветка в списке исключений
1. Нет ли уже подобных вставок (для корректной обработки случая _--amend_ и `git commit -m '<message>'`)

Если проходят все условия, то в начало коммита проставляется номер задачи заданного формата.

## Как использовать

В свой репозиторий необходимо скопировать приведенный выше код в файл _.git/hooks/prepare-commit-msg_ и дать ему права на выполнение:
```shell
$ cd <repository-dir>
$ vim .git/hooks/prepare-commit-msg
<вставка кода>
$ chmod 755 .git/hooks/prepare-commit-msg
```
Далее при каждом коммите в начало сообщения будет подставляться номер задачи в формате **[#задача]**

## Автоматическая установка

Написан [скрипт](https://github.com/Davert94/install-hook) для автоматической установки данного хука
