# Домашнее задание (Пискарев Никита)

## **git clone**
* На самом деле git clone работает как обёртка над некоторыми другими командами. Она создаёт новый каталог, переходит внутрь и выполняет git init для создания пустого репозитория, затем она добавляет новый удалённый репозиторий (git remote add) для указанного URL (по умолчанию он получит имя origin), выполняет git fetch для этого репозитория и, наконец, извлекает последний коммит в ваш рабочий каталог, используя git checkout.
Команда git clone используется в десятке различных мест в этой книге, но мы перечислим наиболее интересные упоминания.

## **git pull**
* Команда git pull работает как комбинация команд git fetch и git merge, т. е. Git вначале забирает изменения из указанного удалённого репозитория, а затем пытается слить их с текущей веткой.
## **git push**
* Команда git push используется для установления связи с удалённым репозиторием, вычисления локальных изменений отсутствующих в нём, и собственно их передачи в вышеупомянутый репозиторий. Этой команде нужно право на запись в репозиторий, поэтому она использует аутентификацию.

# Команды для локального репозитория

## *git init*
Эта команда создаёт в текущем каталоге новый подкаталог с именем .git, содержащий все необходимые файлы репозитория — структуру Git репозитория. На этом этапе ваш проект ещё не находится под версионным контролем. 
Если вы хотите добавить под версионный контроль существующие файлы (в отличие от пустого каталога), вам стоит добавить их в индекс и осуществить первый коммит изменений. Добиться этого вы сможете запустив команду git add несколько раз, указав индексируемые файлы, а затем выполнив git commit:
## *git add*
Команда git add добавляет содержимое рабочего каталога в индекс (staging area) для последующего коммита. По умолчанию git commit использует лишь этот индекс, так что вы можете использовать git add для сборки слепка вашего следующего коммита.
## *git status*
Команда git status показывает состояния файлов в рабочем каталоге и индексе: какие файлы изменены, но не добавлены в индекс; какие ожидают коммита в индексе. Вдобавок к этому выводятся подсказки о том, как изменить состояние файлов.
## *git commit*
Команда git diff используется для вычисления разницы между любыми двумя Git деревьями. Это может быть разница между вашей рабочей копией и индексом (собственно git diff), разница между индексом и последним коммитом (git diff --staged), или между любыми двумя коммитами (git diff master branchB).
## *git log* 
После того, как вы создали несколько коммитов или же клонировали репозиторий с уже существующей историей коммитов, вероятно вам понадобится возможность посмотреть что было сделано — историю коммитов. Одним из основных и наиболее мощных инструментов для этого является команда git log.
## *git checkout*
После того как вы нашли ссылку на нужный коммит в истории, для перехода к нему можно использовать команду git checkout. Команда git checkout — это простой способ «загрузить» любой из этих сохраненных снимков на компьютер разработчика. 
## *git checkout master*  
переключение на ветку master в последний коммит
## *git diff*
Показывает различия между проиндексированной и последней зафиксированной версиями файлов
## *git diff [первая ветка]...[вторая ветка]*
Показывает разницу между содержанием коммитов двух веток
## *git show [коммит]*
Выводит информацию и показывает изменения в выбранном коммите
## *git branch*
Список именованных веток коммитов с указанием выбранной ветки
## *git branch [имя ветки]*
cоздаёт новую ветку

## *git merge [имя ветки]*
Вносит изменения указанной ветки в текущую ветку

## *git branch -d [имя ветки]*
Удаляет выбранную ветку
