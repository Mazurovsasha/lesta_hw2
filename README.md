# Домашняя работа к лекции №2 

## Создайте локальный Git-репозиторий.

```bash
git init
```
## Настройте имя пользователя и email для текущего репозитория.

```bash
git config user.name "Alex Mazurov"
git config user.email "mazurovsasha@gmail.com"
git config --list --local
```
➜  HW2_Lesta git:(master) ✗ git config --list --local
```
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
user.name=Alex Mazurov
user.email=mazurovsasha@gmail.com
(END)
```

## Создайте структуру проекта с несколькими директориями. Добавьте не менее трёх файлов в разные каталоги.

```bash
mkdir 1
echo "Dir 1" > /home/sasha/HW2_Lesta/1/1.txt
mkdir 2
echo "Dir 2" > /home/sasha/HW2_Lesta/2/2.txt
mkdir 3
echo "Dir 3" > /home/sasha/HW2_Lesta/3/3.txt
```

## Настройте .gitignore, исключив один из подкаталогов от отслеживания.

```bash
echo "/1/" > .gitignore
```

```
➜  HW2_Lesta git:(master) ✗ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        2.bmp
        2/
        3/
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

## Создайте две ветки от main: feature/api и feature/ui.

```bash
git branch feature/api
git branch feature/ui
```