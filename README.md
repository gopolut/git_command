
## git commands

+ `git log` выводит список версий сохраненных в данный репозиторий
   + `-p` - разница, внесенная каждым коммитом
   + `-2` - ограничивает выводимый результат
   + `-stat` - краткая статистика по каждой версии
   + `--pretty=format: '%h - %an, %ar : %s'` - вывод записей журнала в выбранном формате
   + `--since --until` - ограничение по времени (--since=2.weeks)
   + `--author` - автор коммита
+ `git diff` выводит измененные строки
   + `--check` - показывает пробелы в коде
+ `git restore <file_name>` отменить изменения, показываемые командой status (если они еще не были закоммичены)
+  `git log --oneline --decorate --graph --all`

## Состояние, отчет:

  + `git status` - отчет о состоянии
    + `-s` - отчет в компактной форме
+ `git diff` - что было изменено, но пока не проиндексировано
   + `--staged` - что из проиндексированного войдет в следующий коммит 


## Удаление файлов

+ `git rm` - удаляет файл из рабочей папки
   + `-f` - принудительное удаление, в т.ч. и из одласти индексирования 
   + `--cached <имя_файла>` - файл остается, но файл игнорируется GITом


+ `git add --patch` - идексация файла по частям
+ `git add :/path/to/files/` - путь относительно корневой директории


| Команда Git           |New files|Modified files|Deleted files|Files with names beginning with a dot|Current directory|Higher  directories|
|------------|-----------|-----------|----------|-----------------|------------|-------------|
|`git add -A`  | Yes 	 |  Yes      |   Yes 	|    Yes 	  |    Yes     |    Yes      |
|`git add .`   | Yes 	 |  Yes      |   Yes 	|    Yes 	  |    Yes     |    No       |
|`git add -u`  | No 	 |  Yes      |	 Yes 	|    Yes 	  |    Yes     |    Yes      |


## Отображение удаленных репозиториев

  + `git remote`: просмотр настроенных удаленных серверов
           `-v` - выводит URL-адреса
  + `git remote show <имя удаленного сервера origin>`: получение инфы о конкретном удаленном сервере
  + `git remote rename <имя_которое_будет_изменено> <новое_имя>`: меняет сокращенные имена удаленных репозиториев


## Просморт удаленных репозиториев

  + `git remote show <имя_удаленного_репозитория> origin` - данные удаленного репозитория
  + `git remote rename <имя_меняемого_репо> <новое_имя_репо>` - смена имени


## Теги

  + `git tag`: добавить тег (теги по умолчанию привязаны к последнему коммиту)
     + `-a` - добавляет коммент к тегу
     + `-m`- сообщение к тегу
  + `git show` - просмотр тега вместе с помеченным им коммитом
  + `git tag -a v0.5 -m 'added file' a5dd2d24` - пометить ранее сделанный коммит тегом
  + `git push origin <имя_тега>` - отправка тега
     + `--tags` - отправка всех тегов


## Псевдонимы

  + `git config --global alias.st status` - псевдоним для комманды status

## Ветвления
```no-highlight
master: f7d4026 -- 8dce2e8 -- 6b9b644
listing:        \ 9a4632c -- 671e87f
```

+ `git branch` - посмотреть в какой ветке вы находитесь
+ `git branch <имя_ветки>` - создание новой ветки
   + `-d <имя_ветки>` - удалить ветку
   + `-v` - показывает последний коммит выполненный в каждой ветке
   + `-vv` - показывает список веток наблюдения
+ `git checkout <имя_ветки>` - переключение на ветку
   + `<имя_коммита>` - перейти на определенный коммит 
   + `-b <имя_ветки>` - сразу переключиться на ветку
+ `git log --oneline --decorate` - показывает куда нацелены указатели веток (HEAD -> master)

+ `git merge <имя_ветки>` - объединение ветки <имя_ветки> с веткой master (предварительно надо переключиться на master)
+ `git clone -o <имя_ветки>` - присвоить новое имя клонируемой ветке
+ `git push origin(удаленный сервер) <имя_ветки>` - отправка ветки на удаленный сервер
+ `git rebase <имя_ветки_откуда_выполняется_перемещение>` - берет изменения в одной ветке и повторяет в другой (в текущей)
