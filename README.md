# Что такое git?

**Система контроля версий (VSC)** - программное обеспечение для работы с изменяющейся информацией
  
# Подготовка репозитория

## *git init*

Команда `git init` создает в директории пустой репозиторий в виде директории .git, где и будет в дальнейшем храниться вся информация об истории коммитов, тегах — о ходе разработки проекта:

    mkdir project-dir
    cd project-dir
    git init

# Создание сохранений

## *git add*

Следующее, что нужно знать — команда `git add`. Она позволяет внести в индекс — временное хранилище — изменения, которые затем войдут в коммит.  
`git add EDITEDFILE` - индексирует измененный файл, либо оповещение о создании нового
`git add .` - вносит в индекс все изменения, включая новые файлы

## *git rm*

Из индекса и дерева проекта одновременно файл можно удалить командой `git rm`.  
`git rm FILE1 FILE2` - удаляет из индекса и дерева проекта отдельные файлы  
`git rm -r --cached .` - вносит в индекс все удаленные файлы

## *git reset*

Сбросить весь индекс или удалить из него изменения определенного файла можно командой `git reset`  
`git reset` - удаляет из индекса конкретный файл:
`git reset — EDITEDFILE`- используется не только для сбрасывания индекса - см.раздел "перемещения между сохранениями"

## *git commit*

Коммит — базовое понятие во всех системах контроля версий, поэтому совершаться он должен легко и по возможности быстро. В простейшем случае достаточно после индексации набрать `git commit`  
`git commit -a` - совершает коммит, автоматически индексируя изменения в файлах проекта. Новые файлы при этом индексироваться не будут, удаление же файлов будет учтено
`git commit -m «commit comment»` - комментирует коммит прямо из командной строки вместо текстового редактора
`git commit FILENAME`- вносит в индекс и создаёт коммит на основе изменений единственного файла

# Перемещения между сохранениями

## *git reset*

`git reset` позволяет сбросить состояние проекта до какого-либо коммита в истории. В git данное действие может быть двух видов: **«мягкого»(soft reset)** и **«жесткого» (hard reset)**.
«Мягкий» (с ключом --soft) резет оставит нетронутыми ваши индекс и все дерево файлов и директорий проекта, вернется к работе с указанным коммитом. «Жесткий» резет (ключ --hard) — команда, которую следует использовать с осторожностью. Она вернет дерево проекта и индекс в состояние, соответствующее указанному коммиту, удалив изменения последующих коммитов  
`git reset --soft HEAD^` - переход к работе над уже совершенным коммитом, сохраняя все состояние проекта и проиндексированные файлы  
`git commit -c ORIG_HEAD` - возврат к последнему коммиту, будет предложено отредактировать его сообщение

## *git revert*

Возможна ситуация, в которой требуется отменить изменения, внесенные отдельным коммитом. `git revert` создает новый коммит, накладывающий обратные изменения

`git revert config-modify-tag` - oтменяет коммит, помеченный тегом

`git revert cgsjd2h` oтменяет коммит, используя его хэш

`git revert cgsjd2h -m 1` для отмены коммита слияния (коммита у которого несколько родителей), необходимо указать хэш и номер одного из родителей коммита.
Для использования команды необходимо, чтобы состояние проекта не отличалось от состояния, зафиксированного последним коммитом.

# Журнал изменений

## *git log*

Иногда требуется получить информацию об истории коммитов; коммитах, изменивших отдельный файл; коммитах за определенный отрезок времени и так далее. Для этих целей используется команда `git log`.

Получает подробную информацию о каждом в виде патчей по файлам из коммитов можно, добавив ключ **-p** (или **-u**): `git log -p`  

Статистика изменения файлов, вроде числа измененных файлов, внесенных в них строк, удаленных файлов вызывается ключом **--stat**: `git log --stat`  

За информацию по созданиям, переименованиям и правам доступа файлов отвечает ключ **--summary**: `git log --summary`  

Чтобы просмотреть историю отдельного файла, достаточно указать в виде параметра его имя: `git log README`

Красивый ASCII-граф коммитов выводится с использованием ключа `--graph`.

# Ветвление в git

## *git branch*

Работа с ветками — очень легкая процедура в git, все необходимые механизмы сконцентрированы в одной команде.

Просто перечисляет существующие ветки, отметив активную:
`git branch`  

Создаёт новую ветку new-branch:
`git branch new-branch`   

Удаляет ветку, если та была залита (merged) с разрешением возможных конфликтов в текущую:
`git branch -d new-branch`  

Удаляет ветку в любом случае:
`git branch -D new-branch`  

Переименовывает ветку:
`git branch -m new-name-branch`

## *git checkout*

команда, запускающая переключение между ветками, извлечение файлов 

## *git merge*  

слияние веток, разрешение возможных конфликтов


# Работа с удаленным репозиторием

## Начало работы, синхронизация репозиториев
    1. Создать аккаунт на GitHub.com
    2. Создать локальный репозиторий в папке
    3. "Подружить" локальный и удаленный репозиторий
    4. Отправить ваш локальный репозиторий в удаленный
    5. Провести изменения с другого компьтера
    6. Загрузить актуальное состояние из удаленного репозитория

## Создание pull request
    1. Делаем fork репозитория
    2. Делаем clone СВОЕЙ версии репозитория
    3. Создаем новую ветку и в НЕЕ вносим свои изменения
    4. Фиксируем изменения (делаем коммиты)
    5. Отправляем свою версию в свой GitHub
    6. На сайте GitHub нажимаем кнопку pull request

## Ключевые команды для работы с удаленным репозиторием
![](git_clone.jpg)
![](git_pull.jpg)
![](git_push.jpg)
