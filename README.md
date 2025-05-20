# Домашняя работа к лекции №2 

## 1. Создайте локальный Git-репозиторий.

```bash
git init
```
## 2. Настройте имя пользователя и email для текущего репозитория.

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

## 3. Создайте структуру проекта с несколькими директориями. Добавьте не менее трёх файлов в разные каталоги.

```bash
mkdir 1
echo "Dir 1" > /home/sasha/HW2_Lesta/1/1.txt
mkdir 2
echo "Dir 2" > /home/sasha/HW2_Lesta/2/2.txt
mkdir 3
echo "Dir 3" > /home/sasha/HW2_Lesta/3/3.txt
```

## 4. Настройте .gitignore, исключив один из подкаталогов от отслеживания.

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
```
➜  HW2_Lesta git:(master) ✗ git add .
➜  HW2_Lesta git:(master) ✗ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   .gitignore
        new file:   2.bmp
        new file:   2/2.txt
        new file:   3/3.txt
        new file:   README.md

➜  HW2_Lesta git:(master) ✗ git commit -m "Задания 1-4"
[master (root-commit) 9c39df1] Задания 1-4
 5 files changed, 68 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 2.bmp
 create mode 100644 2/2.txt
 create mode 100644 3/3.txt
 create mode 100644 README.md
 ```
## 5. Создайте две ветки от main: feature/api и feature/ui.

```bash
git branch feature/api
git branch feature/ui
```

➜  HW2_Lesta git:(master) ✗ git branch
```
  feature/api
  feature/ui
* master
(END)
```

## 6. В каждой ветке внесите независимые изменения. Сделайте как минимум по 2 коммита в каждой ветке с осмысленными сообщениями.

Ветка feature/api

```bash
git checkout feature/api
echo "Задание 6. Изменения в ветке feature/api" >> /home/sasha/HW2_Lesta/1/1.txt
git add .
git commit -m "Задание 6. Изменения в ветке feature/api"
echo "Задание 6. Изменения 2 в ветке feature/api" >> /home/sasha/HW2_Lesta/2/2.txt
<<<<<<< HEAD
git add .
git commit -m "Задание 6. Изменения 2 в ветке feature/api"
```
Веткаа feature/ui

```bash
git checkout feature/ui
echo "Задание 6. Изменения в ветке feature/ui" >> /home/sasha/HW2_Lesta/3/3.txt
git add .
git commit -m "Задание 6. Изменения 1 в ветке feature/ui"
echo "Задание 6. Изменения 2 в ветке feature/ui" >> /home/sasha/HW2_Lesta/3/3.txt
git add .
git commit -m "Задание 6. Изменения 2 в ветке feature/ui"
```

## 7. Выполните слияние ветки feature/api в main с использованием --no-ff.

```bash
git checkout master
git merge --no-ff feature/api -m "Слияние ветки feature/api в master"
git log --graph --oneline
```
