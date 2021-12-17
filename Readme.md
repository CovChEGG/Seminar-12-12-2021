# Инструкция по работе с Git и удалёнными репозиториями

## Что такое Git?

Git - одна из реализаций распределённых систем контроля версий, имеющая как лольную версионность, так и версионность на сервере. Git является самой популярной системой контроля версий на сегодняшний день.

## Подготовка репозитория
Для того, чтобы создать репозиторий в указанной папке используется команда *git init*. Для этого достаточно написать команду *git init* в папке с будущем репозиторием

## Создание фиксаций
### Просмотр информации о изменениях

Для того, чтобы посмотреть информацию об изменениях, сделанных в текущей ветке, необходимо использовать команду *git status*. Для этого достаточно использовать *git status* в папке с репозиторием

### Добавление файла к коммиту
Для того, чтобы добавить файл к новому коммиту("сохранению") необходимо использовать команду *git add*. Используется она следующим образом: в папке с репозиторием пишем команду *git add <имя файла>*

### Создание коммитов

Для создания новой фиксации необходимо использовать команду *git commit*. Используется она следующим образом: в папке с репозиторием пишется команда *git commit -m "<сообщение к коммиту>"*. Все файлы коммита должны быть предворительно добавлены с помощью команды *git add*. Сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***

## Перемещение между сохранениями
Для перемещения между коммиитами необходимо использовать команду *git checkout*. Используется она следующим образом в папке с репозиторием: *git checkout <номер комиита>*.

## Журнал изменений
Для просмотра журнала изменений необходимо использовать команду *git log*. Для этого нужно в папке с репозиторием написать *git log*

## Ветки в Git
### Создание веток в Git
Для того, чтобы создать новую ветку необходимо использовать команду *git brnach*. Используется она следующим образом в папке с репозиторием: *git branch <название ветки>*.
### Просмотр списка веток
Для того, чтобы просмотреть список веток необходимо использовать команду *git branch*. Для этого в папке с репозиторием надо набрать команду *git branch*

### Переход между ветками
Для того, чтобы перейти на другую ветку необходимо использовать команду *git checkout*. Используется она в папке с репозиторием следующим образом: *git checkout <название ветки>*.

## Слияние веток и разрешение конфликтов
### Слияние веток
Для слияния веток необходимо использовать команду *git merge*. Используется она следующим образом: Для начала ***ОБЯЗАТЕЛЬНО*** перейти на ветку, куда мы сливаем изменения, после чего надо воспользоваться командой *git merge <название сливаемой ветке>*. Слияние может произойти автоматически, а может вознить конфликт. Про разрешение конфликтов смотри дальше.

## Удаление веток

## Работа с удаленными репозиториями

### Что такое удаленный репозиторий и для чего он нужен

Для того, чтобы иметь возможность совместно с другими пользователями работать в каком-либо Git-проекте, необходимо использовать удалённые репозитории. Удалённые репозитории представляют собой версии проектов, сохранённых в интернете или ещё где-то в сети.

### Базовая работа с удаленными репозиториями GitHub

#### Просмотр удалённых репозиториев

Для того, чтобы просмотреть список настроенных удалённых репозиториев, необходимо выполнить команду: `git remote`. Если репозиторий был клонирован, то на экране появится как минимум `origin` - имя по умолчанию, которое Git даёт серверу, с которого производилось клонирование (с помощью комманды `git clone <адерс удалённого репозитория>`)

Для того, чтобы чтобы просмотреть адреса для чтения и записи, привязанные к репозиторию необходимо использовать команду: `git remote -v`

    git remote -v
    origin  https://github.com/CovChEGG/Seminar-12-12-2021.git (fetch)
    origin  https://github.com/CovChEGG/Seminar-12-12-2021.git (push)

Где `fetch` - отображает адрес для извлечения, а `push`- отображает адрес для отправки, при этом вывод команды не даёт никакой информации о правах доступа (только адрес и назначение).

Более подрробную информацию можно узнать по команде `git remote show <удалённый репозиторий>`.

#### Добавление удалённых репозиториев

Чтобы добавить удалённый репозиторий и присвоить ему имя (короткое_имя), просто выполните команду:
`git remote add <короткое_имя> <адрес репозитория>`
В дальнейшем, чтобы обращаться к удалённому репозиторию можно исользовать указанное в команде `<короткое_имя>`.  
При использовании команды `git clone` (помимо всех её действий) происходит добавление удалённого сервера и связь с локальным репозиторием с присвоением короткого имени `origin`.

#### Получение изменений из удалённого репозитория

Для получения данных из удалённых проектов, следует выполнить команду:  
`git fetch [короткое_имя или адрес репоизтория]`
Данная команда связывается с указанным удалённым проектом и забирает все те данные проекта, которых у нас ещё нет. После выполнения команды, у нас должны появиться ссылки на все ветки из этого удалённого проекта, которые можно будет просмотреть или слить в любой момент.
**Важно!!!** что команда git fetch забирает данные в локальный репозиторий, но не сливает их с какими-либо локальными наработками и не модифицирует то, над чем происходит работа в данный момент. Нам необходимо вручную сливать эти данные с локальными, когда это понадобится.

Если ветка настроена на отслеживание удалённой ветки, то можно использовать команду `git pull` чтобы автоматически получать изменения из удалённой ветки и сливать их со своей текущей. Этот способ может оказаться более простым или более удобным. К тому же, по умолчанию команда `git clone` автоматически настраивает нашу локальную ветку master на отслеживание удалённой ветки master на сервере, с которого происходило клонирование репозитория. Название веток может быть другим и зависит от ветки по умолчанию на сервере. Выполнение git pull, как правило, извлекает (fetch) данные с сервера, с которого мы изначально клонировали, и автоматически пытается слить (merge) их с кодом, над которым в данный момент работаем.

#### Отправка изменений в удаленный репозиторий

Для того, чтобы поделиться нашими наработаками с другими, нобходимо отправить наши данные в удалённый репозиторий. Для этого исполтзуется команда `git push <удаленный репозиторий> <ветка удалённого репозитория>`.   
Например, чтобы отправить ветку master на сервер origin (клонирование обычно настраивает оба этих имени автоматически), можно выполнить следующую команду для отправки произведённых коммитов: `git push origin master`.  
Эта команда срабатает только в случае, если мы изначально закачивали первоначальные данные или клонировали их с сервера, на котором у нас есть права на запись, и если никто другой с тех пор не выполнял команду push. Если кто-то ещё одновременно имеет доступ на изменение ветки (например клонирует её), затем он выполняет команду push, то после него выполнить команду push нам не удастся, наша команда точно будет отклонена. Придётся сначала получить изменения и объединить их с вашими (например с помощью команды `git pull`) и только после этого можно будет выполнить push.



###### The end
