---
title: Введение в командную оболочку
# teaching: 5
# exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Объяснить, как командная оболочка взаимодействует с клавиатурой, экраном, операционной системой и пользовательскими программами.
- Объяснить, когда и почему следует использовать интерфейсы командной строки вместо графических интерфейсов.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- Что такое командная оболочка и зачем она может понадобиться?

::::::::::::::::::::::::::::::::::::::::::::::::::

### Введение

Люди и компьютеры обычно взаимодействуют различными способами: с помощью клавиатуры и мыши, сенсорных экранов или систем распознавания речи. Наиболее распространённым способом взаимодействия с персональными компьютерами является **графический пользовательский интерфейс** (**graphical user interface**, **GUI**). В GUI команды передаются через клики мышью и меню.

Несмотря на то, что GUI интуитивно понятен, такой способ взаимодействия плохо масштабируется. Представьте задачу: вам нужно скопировать третью строку из тысячи текстовых файлов, расположенных в разных папках, и вставить их в один файл. Используя GUI, вы бы кликами потратили часы и могли бы совершить ошибку. В таких случаях приходит на помощь командная оболочка Unix. Она является **интерфейсом командной строки** (**command-line interface**, **CLI**) и языком сценариев (скриптов), что позволяет выполнять повторяющиеся задачи быстро и в автоматическом режиме. С правильными командами оболочка может повторять операции с необходимыми изменениями столько раз, сколько потребуется. В приведённом примере с файлами задача выполняется за секунды.

### Оболочка

**Оболочка** (**Shell**) — это программа, в которой пользователи вводят команды. С её помощью всего одной строкой кода можно запускать как сложные программы, наподобие программы для моделирования климата, так и простые команды для создания пустых папок. Самая популярная оболочка Unix — это **Bash** (**Bourne Again SHell**), которая создана на основе оболочки Стивена Борна. Bash — это оболочка по умолчанию во многих системах Unix, а также в пакетах Unix-подобных инструментов для Windows (например, Git Bash).

Работа с оболочкой требует времени на изучение. В отличие от графического интерфейса, где доступные операции находятся на виду у пользователя, в интерфейсе командной строки они не показываются автоматически, поэтому команды учатся подобно новым словам в незнакомом языке. Однако, даже небольшой набор команд позволяет выполнять широкий спектр задач, и сегодня мы рассмотрим самые важные из них.

Синтаксис командной оболочки позволяет комбинировать существующие инструменты в мощные последовательности операций и обрабатывать большие объёмы данных автоматически. Последовательности команд могут быть сохранены в виде скриптов, что повышает воспроизводимость рабочих процессов.

Кроме того, командная строка — это часто самый простой способ взаимодействия с удалёнными машинами и суперкомпьютерами. Знание оболочки является ключевым при работы с специализированными инструментами и высокопроизводительными системами. По мере распространения облачных и кластерных вычислений, навыки работы с оболочкой становятся всё более востребованными для решения научных и вычислительных задач.

Итак, приступим.

Когда оболочка запускается, появляется приглашение (**prompt**), которое показывает, что оболочка ожидает ввода:

```bash
$
```

Обычно в качестве приглашения используется символ `$`, но это может быть другой символ. В примерах этого урока приглашение будет показано как `$`. Важно **не вводить** сам символ `$`, когда вы набираете команды, а только то, что следует за ним. Это правило действует как в данном уроке, так и в других материалах. Также стоит отметить, что после ввода команды, необходимо нажать на клавишу <kbd>Enter</kbd>, чтобы исполнить её.

Приглашение сопровождается **текстовым курсором**, который показывает, где будет появляться ваш ввод. Курсор может быть мигающим блоком, подчёркиванием или вертикальной чертой. Вы могли видеть его в текстовых редакторах.

Ваше приглашение может выглядеть иначе, например, может содержать имя пользователя и хоста (имени компьютера в используемой сети):

```bash
nelle@localhost $
```

Приглашение может включать и большее количество информации (и даже располагаться в несколько строк). Не беспокойтесь, если приглашение представляет собой не просто символ `$`. Данный урок не будет полагаться на эту дополнительную информацию. Единственное на что пока стоит обращать внимание в приглашении — это непосредственно символ `$` и позже мы разберёмся почему.

Теперь попробуем нашу первую команду ls, которая выводит список содержимого текущей директории:

```bash
$ ls
```

```output
Desktop     Downloads   Movies      Pictures
Documents   Library     Music       Public
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Команда не найдена

Если оболочка не может найти программу с введённым именем команды, она выведет сообщение об ошибке:

```bash
$ ks
```

```output
ks: command not found
```

Это может произойти, если команда введена неправильно или соответствующая программа не установлена.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Пример задачи Нелли

Нелли Немо, морской биолог, вернулась после шестимесячного исследования [Северо-Тихоокеанского течения](https://ru.wikipedia.org/wiki/Северо-Тихоокеанское_течение), где она собирала образцы медуз в [Большом тихоокеанском мусорном пятне](https://ru.wikipedia.org/wiki/Большое_тихоокеанское_мусорное_пятно). У неё есть 1520 образцов, которые она исследовала на анализаторе, измеряющем относительное содержание 300 белков. Ей нужно обработать полученные файлы с помощью программы `goostats.sh`, но у неё также есть статья, которую нужно написать до конца месяца для публикации в спец-выпуске журнала _"Записки о жиже"_.

Если бы Нелли запускала `goostats.sh` вручную через GUI, ей пришлось бы открывать файлы 1520 раз. Исходя из того, что `goostats.sh` требуется порядка 30с для обработки каждого файла, весь этот процесс потребовал бы более 12 часов внимания Нелли. С использованием оболочки она может автоматизировать этот процесс и сосредоточиться на написании статьи.

Далее будет рассмотрено, как Нелли может использовать оболочку для автоматизации этой задачи. В частности, как использовать оболочку для запуска программы `goostats.sh`, использовать циклы для автоматизации повторяющихся этапов ввода имён файлов так, чтобы поручить выполнение этой задачи компьютеру, пока Нелли сможет сосредоточиться на написании её статьи.

И в качестве бонуса: однажды автоматизировав этот процесс, Нелли сможет повторить его когда угодно, в случае, если у нее получится собрать новые образцы.

Чтобы выполнить задачу, Нелли нужно уметь:

- перемещаться по файловой системе
- создавать файлы/каталоги
- проверять длину файла
- объединять команды в цепочки
- извлекать набор файлов
- использовать циклы для повторения команд
- запускать скрипты

:::::::::::::::::::::::::::::::::::::::: keypoints

- Оболочка — это программа, основная задача которой — обработка команд и запуск других программ.
- Этот урок использует Bash — оболочку, используемую по умолчанию во многих Unix-системах.
- Программы в Bash запускаются через интерфейс командной строки.
- Основные преимущества оболочки — высокая эффективность ввода команд, автоматизация повторяющихся задач и доступ к удалённым компьютерам.
- Одной из сложностей работы с оболочкой является знание нужных команд и их правильного использования.

::::::::::::::::::::::::::::::::::::::::::::::::::
