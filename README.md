# Работа с Git с примерами

## Навигация  
- `pwd` (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;  
- `ls` (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;  
- `ls -a` — покажи также скрытые файлы и папки, названия которых начинаются с символа `.`;  
- `cd first-project` (от англ. change directory, «сменить директорию») — перейди в папку first-project;  
- `cd first-project/html` — перейди в папку html, которая находится в папке first-project;  
- `cd ..` — перейди на уровень выше, в родительскую папку;
- `cd ~` — перейди в домашнюю директорию (/Users/Username);
- `cd /` — перейди в корневую директорию.

## Работа с файлами и папками  
### Создание  
- `touch index.html` (англ. touch, «коснуться») — создай файл index.html в текущей папке;  
- `touch index.html style.css script.js` — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;  
- `mkdir dir` (от англ. make directory, «создать директорию») — создай папку с именем dir в текущей папке;  
- `mkdir -p dir/dir-inside/dir-deeper-inside` — создай папку dir, в которой создай папку dir-inside, в которой создай папку dir-deeper-inside.

### Копирование и перемещение  
- `cp file.txt ~/my-dir` (от англ. copy, «копировать») — скопируй файл в другое место;  
- `mv file.txt ~/my-dir` (от англ. move, «переместить») — перемести файл или папку в другое место.

### Чтение  
- `cat file.txt` (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.

### Удаление  
- `rm about.html` (от англ. remove, «удалить») — удали файл about.html;  
- `rmdir images` (от англ. remove directory, «удалить директорию») — удали папку images;  
- `rm -r project` (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку project и всё, что она содержит.

## Инициализация репозитория  
- `git init` (от англ. initialize, «инициализировать») — инициализируй репозиторий.

## Подготовка файла к коммиту  
- `git add todo.txt` (от англ. add, «добавить») — подготовь файл todo.txt к коммиту;  
- `git add --all` (от англ. add, «добавить» + all, «всё») — подготовь к коммиту сразу все файлы, в которых были изменения, и все новые файлы;  
- `git add .` — подготовь к коммиту текущую папку и все файлы в ней.

## Создание коммита  
- `git commit -m "Комментарий к коммиту."` (от англ. commit, «совершать», «фиксировать» + message, «сообщение») — сделай коммит и оставь комментарий, чтобы было проще понять, какие изменения внесены.

## Просмотр информации о коммитах  
- `git log` (от англ. log, «журнал [записей]») — выведи подробную историю коммитов;  
- `git log --oneline` - выведи сокращённый лог (при этом в терминале появятся только первые несколько символов хеша каждого коммита и комментарии к ним, команда `git log --oneline` автоматически подбирает такую длину сокращённых хешей, чтобы они были уникальными в пределах репозитория).

## Просмотр состояния файлов  
- `git status` (от англ. status, «статус», «состояние») — покажи текущее состояние репозитория.

## Работа с удалённым репозиторием  
- `git remote add origin git@github.com:name/repository.git` (от англ. remote, «удалённый» + add, «добавить») — привяжи локальный репозиторий к удалённому с URL https://github.com/name/repository.git;  
- `git remote -v` (от англ. verbose, «подробный») — проверь, что репозитории действительно связались;  
- `git push -u origin main` (от англ. push, «толкать») — в первый раз загрузи все коммиты из локального репозитория в удалённый с названием origin (для последующих загрузок достаточно `git push`);  
- `git clone git@github.com:name/repository.git` (от англ. clone — «клон», «копия») — склонируй репозиторий с repository.git из аккаунта name на мой локальный компьютер.

## Хеш  
- Хеширование (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint). Git хеширует (преобразует) данные коммита с помощью алгоритма SHA-1 (от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого коммита свой уникальный хеш — результат хеширования. Это целое число, результат хеширования в Git — символьная строка. Она относительно коротка (40 символов в случае SHA-1) и состоит из цифр 0—9 и латинских букв A—F (неважно, заглавных или строчных).

### Свойства хеша  
- Если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый.
- Если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).

### Хеш-таблица  
- Git хранит таблицу соответствий хеш → информация о коммите. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. Можно сказать, что хеш — основной идентификатор коммита.  
- Все хеши и таблицу хеш → информация о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке .git в репозитории проекта.

## HEAD  
- Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).  
- Внутри HEAD — ссылка на служебный файл: refs/heads/master (или refs/heads/main в зависимости от названия ветки).  
- Его можно передать в качестве параметра командам вместо хеша последнего коммита.

## Статусы файлов  
- untracked (англ. «неотслеживаемый») - новые файлы в Git-репозитории помечаются как untracked, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла нет предыдущих версий, зафиксированных в коммитах или через команду git add;   
- staged (англ. «подготовленный») - после выполнения команды git add файл попадает в staging area (от англ. stage — «сцена», «этап процесса» и area — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии staged;  
- tracked (англ. «отслеживаемый») - состояние tracked — это противоположность untracked. В него попадают файлы, которые уже были зафиксированы с помощью git commit, а также файлы, которые были добавлены в staging area командой git add. То есть все файлы, в которых Git так или иначе отслеживает изменения;  
- modified (англ. «изменённый») - состояние modified значит, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.

### Жизненный цикл файлов  

```mermaid
graph LR;
%% Подготовка нового файла к коммиту
  untracked -- "git add" --> staged;
  
%% Коммит
  staged -- "git commit" --> tracked/comitted;
  
%% Изменение
  tracked -- "изменение отслеживаемого файла" --> modified;
  
%% Подготовка изменённого файла к коммиту
  modified -- "git add" --> staged;
```

## Оформление сообщений к коммитам  
### Корпоративный  
Во многих компаниях применяется Jira — система для организации проектов и задач. У каждой задачи в Jira есть идентификатор из нескольких заглавных латинских букв и номера. Например, LGS-239 значит, что это 239-я задача в проекте LGS (сокращение от англ. logistics — «логистика»).
В корпоративном стиле в начале сообщения обычно указывают Jira-ID, а после — текст сообщения.

```bash
$ git commit -m "LGS-239: Дополнить список пасхалок новыми числами"
```

### Conventional Commits  
Стандарт Conventional Commits (англ. «соглашение о коммитах») отличается качественной документацией и подробной проработкой. Он подходит для репозиториев с исходным кодом программ. А вот использовать его для других типов проектов было бы неудобно.
Conventional Commits предлагает такой формат коммита: <type>: <сообщение>. Первая часть type — это тип изменений.
Примеры type:  
- feat (сокращение от англ. feature) — для новой функциональности;  
- fix (от англ. «исправить», «устранить») — для исправленных ошибок.

```bash
git commit -m "feat: добавить подсчёт суммы заказов за неделю"
```

### GitHub-стиль  
GitHub можно использовать не только для хранения файлов проекта, но и для ведения списка задач (англ. issue) этого проекта. Если коммит «закрывает» или «решает» какую-то задачу, то в его сообщении удобно указывать ссылку на неё. Для этого в любом месте сообщения нужно указать #<номер задачи>.

```bash
$ git commit -m "Исправить #334, добавить график температуры"
```
