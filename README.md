![Gitlogo](https://res.cloudinary.com/practicaldev/image/fetch/s--bjpVKHPe--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/8ogqpfkvqqpyfbs3w6p7.png)
# Работа с удаленными репозиториями

_Для того, чтобы внести вклад в какой-либо Git-проект, вам необходимо уметь работать с удалёнными репозиториями. Удалённые репозитории представляют собой версии вашего проекта, сохранённые в интернете или ещё где-то в сети. У вас может быть несколько удалённых репозиториев, каждый из которых может быть доступен для чтения или для чтения-записи. Взаимодействие с другими пользователями предполагает управление удалёнными репозиториями, а также отправку и получение данных из них. Управление репозиториями включает в себя как умение добавлять новые, так и умение удалять устаревшие репозитории, а также умение управлять различными удалёнными ветками, объявлять их отслеживаемыми или нет и так далее._

## Просмотр удаленных репозиториев

_Для того, чтобы просмотреть список настроенных удалённых репозиториев, вы можете запустить команду `git remote`. Она выведет названия доступных удалённых репозиториев. Если вы клонировали репозиторий, то увидите как минимум `origin` — имя по умолчанию, которое Git даёт серверу, с которого производилось клонирование:_

    $ git clone https://github.com/reponame
    Cloning into 'reponame'...
    remote: Reusing existing pack: 1857, done.
    remote: Total 1857 (delta 0), reused 0 (delta 0)
    Receiving objects: 100% (1857/1857), 374.35 KiB | 268.00 KiB/s, done.
    Resolving deltas: 100% (772/772), done.
    Checking connectivity... done.
    $ cd reponame
    $ git remote
    origin

>Команда `cd` обозначает change directory(смена директории репозитория)

> Также можно применить ключ `-v`, чтобы просмотреть адреса для чтения и записи, привязанные к репозиторию:

##  Клонирование удаленного репозитория
![Clone](https://res.cloudinary.com/practicaldev/image/fetch/s--dTbOGQ7K--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/tk6mspyqpuohkynw4wft.png)

Команда `git clone`позволяет клонировать удаленный репозиторий на локальное хранилище для дальнейшей работы и взаимодействием с ним.

    git clone https://github.com/libgit/libgit

## Добавление удалённых репозиториев

_Для того, чтобы добавить удалённый репозиторий и присвоить ему имя (shortname), необходимо выполнить команду `git remote add <shortname> <url>`:_

    $ git remote
    origin
    $ git remote add pb https://github.com/reponame
    $ git remote -v
    origin  https://github.com/reponame (fetch)
    origin  https://github.com/reponame(push)
    pb  https://github.com/reponame(fetch)
    pb  https://github.com/reponame(push)

_Теперь вместо указания полного пути вы можете использовать pb. Например, если вы хотите получить изменения, которые есть у User, но нету у вас, вы можете выполнить команду git fetch pb:_

## Получение изменений из удалённого репозитория — Fetch и Pull

![PushPull](https://blog.axosoft.com/wp-content/uploads/2018/05/push-and-pull.png)

_Для получения данных из удалённых проектов, следует выполнить:_

    $ git fetch [remote-name]

_Данная команда связывается с указанным удалённым проектом и забирает все те данные проекта, которых у вас ещё нет. После того как вы выполнили команду, у вас должны появиться ссылки на все ветки из этого удалённого проекта, которые вы можете просмотреть или слить в любой момент._

_Когда вы клонируете репозиторий, команда clone автоматически добавляет этот удалённый репозиторий под именем «origin». Таким образом, `git fetch origin` извлекает все наработки, отправленные на этот сервер после того, как вы его клонировали (или получили изменения с помощью `fetch`). Важно отметить, что команда `git fetch` забирает данные в ваш локальный репозиторий, но не сливает их с какими-либо вашими наработками и не модифицирует то, над чем вы работаете в данный момент. Вам необходимо вручную слить эти данные с вашими._

_Если ветка настроена на отслеживание удалённой ветки, то вы можете использовать команду `git pull` чтобы автоматически получить изменения из удалённой ветки и слить их со своей текущей._

## Отправка изменений в удаленный репозиторий

_Когда вы хотите поделиться своими наработками, вам необходимо отправить их в удалённый репозиторий. Команда для этого: `git push <remote-name> <branch-name>`. Чтобы отправить вашу ветку master на сервер origin, вы можете выполнить следующую команду для отправки ваших коммитов:_

    $ git push origin master

## Просмотр удаленного репозитория

_Если хотите получить больше информации об одном из удалённых репозиториев, вы можете использовать команду `git remote show <remote>`. Выполнив эту команду с некоторым именем, например, `origin`, вы получите следующий результат:_

    $ git remote show origin
    * remote origin
    Fetch URL: https://github.com/reponame
    Push  URL: https://github.com/reponame
    HEAD branch: master
    Remote branches:
        master                               tracked
        dev-branch                           tracked
    Local branch configured for 'git pull':
        master merges with remote master
    Local ref configured for 'git push':
        master pushes to master (up to date)

## Удаление и переименовывание удаленного репозитория
![remove](https://s3.ap-south-1.amazonaws.com/s3.studytonight.com/tutorials/uploads/pictures/1624367010-103268.png)

_Для переименования удалённого репозитория можно выполнить `git remote rename`. Например, если вы хотите переименовать pb в user, вы можете это сделать при помощи `git remote rename`:_

    $ git remote rename pb user
    $ git remote
    origin
    user

_Для удаление удаленного репозитория вы можете использовать `git remote rm`:_

    $ git remote remove user
    $ git remote
    origin 
